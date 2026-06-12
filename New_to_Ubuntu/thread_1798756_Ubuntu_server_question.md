---
title: "Ubuntu server question"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by ZoeFken on 2011-07-06
Hey everyone

I would like some info about ubuntu server and some advice aswell.

We are starting a company but we are discusing the fact of using ubuntu server or windows server. And there is only one issue we can't figure out at this moment.

We have our own software in development that is required to work on windows systems. The software is required to work in co existence with a server to store data and retrieve if necesary. But we are wondering if this can be done and if there is a way to update our windows software threw ubuntu like it would work with a windows server.

I hope someone can give us some advice and maybe show us a good way to do this.

With kind regards

Me

---

### Post by ZoeFken on 2011-07-06
Bumb for first page

---

### Post by stlsaint on 2011-07-06
Are you asking if ubuntu can update a windows server or if ubuntu can run your software?? 

Please express a little more detail on the software and your current setup. 
Also you should post this in the server section of the forum.

---

### Post by SeijiSensei on 2011-07-06
> **ZoeFken said:**
> The software is required to work in co existence with a server to store data and retrieve if necesary. But we are wondering if this can be done and if there is a way to update our windows software threw ubuntu like it would work with a windows server.

Are you talking simply about writing data to a server-based network share, or something like communicating with an SQL database? 

There are solutions to both cases; Samba for file-sharing, ODBC for SQL.  But it seems to me that you should be asking about what your customers are going to be using.  You want to build one or more models of likely customer configurations in-house and work with them.

As an example, I started an Internet consulting firm back in 1994.  At the time everyone used Novell Netware, so we did, too.  We used Linux for all the Internet-facing services, but we really needed to know how to integrate Linux into Netware networks, because that's what our customers would have on-site.

So what's your market?  What do they run?

---

### Post by ZoeFken on 2011-07-06
No let me explain a bit more in detail.

We wil be offering a real time service to customers ( company's ). Our personal wil need to be able to report what has happend to us and our customers. This wil be done with a software that is beeing developd. Our customers wil get a small part of the program so they can read the data our personal deposits in the server.

We are only wondering if ubuntu server can,

1. Handel trafic between a windows software and a data table ( sql maybe ).
2. It can update the software whithout any intervention of a fysical person. ( with exception of the security measures of the company ofcourse; like internet settings and stuff like that )

Most of the company's around the world stil use windows unless your talking about specific IT companies they seem to have turnd towards linux ( with good reason ). We are intending to make a linux version of our software in the future, but curently we need to focus to the biggest part of our market.

I hope you can advice as this would be much appreciated.

---

### Post by ZoeFken on 2011-07-07
Bump i stil need info :)

---

### Post by mikejonesey on 2011-07-07
as regards 1. Handel trafic between a windows software and a data table ( sql maybe ).

sure, you can write a server side prog in a number of languages to handle different requests from your software.

2. It can update the software whithout any intervention of a "fysical"  person.

a little vague lol but yes you can host updates which your software can access and use as an update.

most of what you are after will be developed into your software rather than on the server...

---

