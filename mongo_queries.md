##Provide a query showing just the names (and nothing else) of the Italian restaurants.
db.restaurants.find({}, {name: 1})

##Provide a query showing how many Bakeries have a name that start with M.
db.restaurants.find({$and: [{cuisine: "Bakery"}, {name: /^M/}]}).count()

##Provide a query showing the zip codes (and _id's) of all restaurants with the word "Ice" in their cuisine.
db.restaurants.find({cuisine: /Ice/}, {"address.zipcode": 1})

##Provide a query showing the street and street number of Chinese restaurants ordered by zip code.
db.restaurants.find({cuisine: "Chinese"}, {"address.street": 1}).sort({"address.zipcode": 1})

##Show only the American restaurants in Manhattan.
db.restaurants.find({"borough": "Manhattan", "cuisine": "American "})

##Provide a query showing the restaurants that have been graded exactly 4 times.
db.restaurants.find({grades: {$size: 4}})

##Provide a query showing only _id, name and 2 grades from each restaurant on Broadway.
db.restaurants.find({"address.street": /Broadway/}, { grades: { $slice: 2 }, name: 1 })

##Provide a query showing the 5 pizza restaurants in the Bronx with the highest score on an evaluation.
 db.restaurants.find({cuisine: /Pizza/, borough: "Bronx"})

##Provide a query to find all of the restaurants in Brooklynn and list only the 21st-30th results when ordered alphabetically by name.
db.restaurants.find({borough: "Brooklyn", name: /^[A-Za-z][A-Za-z0-9]/}, {name: 1}).sort({"name": 1}).skip(20).limit(10)

