---
title: "Applications requiring authentication through squid"
date: 2014-10-31
forum: Networking &amp; Wireless
---

### Post by John_Haswell on 2014-10-31
We are having issues with programs needing to authenticate with squid. Can you advise how I go about allowing them through or stopping the need for authentication?

 I think you can do an acl but how can I do a specific acl for a program that I have? 

 These programs are as follows
 Staffplan
 Bing maps
 Java
 Bond

 There are others and the list is growing each week. 

 We use Squidclam av and also qlproxy

 Please help

---

### Post by SeijiSensei on 2014-10-31
I can see writing ACLs based on remote domains or URLs you need to access as in the case of Bing maps.  

If by Java you mean programs that download and run remote Java objects, you might be able to write an ACL based on the object's mimetype, like "application/java-archive."

---

