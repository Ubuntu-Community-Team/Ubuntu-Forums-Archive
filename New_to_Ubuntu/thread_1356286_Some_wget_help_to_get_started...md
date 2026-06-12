---
title: "Some wget help to get started.."
date: 2009-12-15
forum: New to Ubuntu
---

### Post by hopelessone on 2009-12-15
Hi,

I used to use Ofline Explorer, Nowdays i want to use wget...
Can you help me get this straight?

The Website:
```
http://uk.yachtworld.com/core/listing/cache/searchResults.jsp?fromLength=30&slim=quick&Ntk=boatsUK&searchtype=homepage&type=%28Sail%29&sm=3&cit=true&toLength=30&luom=126&currencyid=1005&No=0&ps=50
```

I want to download all .jpg pictures of 30' yachts and put them all in 1 directory

Total yachts 1,460 in increments of 50 from the end of the web add. (ps=50)(ps=100)etc..

then only follow the links on that page to [http://uk.yachtworld.com/boats/*](http://uk.yachtworld.com/boats/*) 
then download those pictures from [http://uk.yachtworld.com/core/listing/displayPhoto.jsp](http://uk.yachtworld.com/core/listing/displayPhoto.jsp) ending in .jpg 1 deep

I confused myself i got:
```
wget -r  http://uk.yachtworld.com/core/listing/cache/searchResults.jsp?fromLength=30&slim=quick&Ntk=boatsUK&searchtype=homepage&type=%28Sail%29&sm=3&cit=true&toLength=30&luom=126&currencyid=1005&No=0&ps=50
```

then in a .wgetrc file:
```
--no-directories 
--no-parent
--accept .jpg 
--include list http://uk.yachtworld.com/core/listing/displayPhoto.jsp
```

What else is there to do?

Thanks for reading..

---

