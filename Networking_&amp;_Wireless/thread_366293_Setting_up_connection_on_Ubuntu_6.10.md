---
title: "Setting up connection on Ubuntu 6.10"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by duvkata on 2007-02-20
I have a little problem setting up my connection on ubuntu and i`ll be very grateful if someone can help me.Because I`m a little bit new with Linux,I would like to show you the steps given by my ISP of how to configure my connection for Windows and when you read it you can tell me what to do on Ubuntu.I should mention that I already tried to connect,but something is wrong,that`s why I`m posting here this topic.The problem is that in my distribution(version) i don`t have the file /etc/ppp/pppoe.conf but instead a file named options that is little different and there`s missing a thing called SERVICE_NAME which is needed to set up my connection.So here are the steps for Windows hope you understand and help me.
1.Create New Network Connection -> Next
2.Choose type of connection -> Connect to the Internet -> Next
3.How do you want to connect to the Internet -> Set up my connection manualy -> Next
4.Choose -> Connect using a broadband connection that requires username and pass -> Next
5.ISP name -> "type anything" -> Next -> Adding Username and password -> Next -> Finish
6.Then choose Properties on the created Connection **and here`s the imporant thing.In the GENERAL Tab,in the field called Service Name I should type "Slatina1",or else it will not work.This is the same thing that I can`t figure out where is on Ubuntu.**
Hope that someone have experienced that problem before and can tell me how to fix things out.Thanks in advance,sorry if that is a stupid question or I sound like some lamer :) and sorry for my bad english...

---

### Post by duvkata on 2007-02-20
can`t nobody help yet ?

---

### Post by Strider on 2007-02-20
Hi,

Is your Broadband Provider using PPPoE connection?  Seems like it is.  Take a look at the following guide and check under PPPoE:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Also, do a search for PPPoE in the forums and hopefully that'll help you out.  One way to not do the settings it to setup a router at home.  Preferred way to go anyway... router will take all the hits from the outside and your PCs will be protected inside.  Also, allows you to share the single connection -- just a suggestion.

-Mike

---

### Post by RedSquirrel on 2007-02-20
> **duvkata said:**
> I have a little problem setting up my connection on ubuntu and i`ll be very grateful if someone can help me.Because I`m a little bit new with Linux,I would like to show you the steps given by my ISP of how to configure my connection for Windows and when you read it you can tell me what to do on Ubuntu.I should mention that I already tried to connect,but something is wrong,that`s why I`m posting here this topic.The problem is that in my distribution(version) i don`t have the file /etc/ppp/pppoe.conf but instead a file named options that is little different and there`s missing a thing called SERVICE_NAME which is needed to set up my connection.So here are the steps for Windows hope you understand and help me.
1.Create New Network Connection -> Next
2.Choose type of connection -> Connect to the Internet -> Next
3.How do you want to connect to the Internet -> Set up my connection manualy -> Next
4.Choose -> Connect using a broadband connection that requires username and pass -> Next
5.ISP name -> "type anything" -> Next -> Adding Username and password -> Next -> Finish
6.Then choose Properties on the created Connection **and here`s the imporant thing.In the GENERAL Tab,in the field called Service Name I should type "Slatina1",or else it will not work.This is the same thing that I can`t figure out where is on Ubuntu.**
Hope that someone have experienced that problem before and can tell me how to fix things out.Thanks in advance,sorry if that is a stupid question or I sound like some lamer :) and sorry for my bad english...

Have you tried to create the /etc/ppp/pppoe.conf file manually and adding

```

servicename "Slatina1"

```Did you try:

```
sudo pppoeconf
```Even if you can't connect after doing that, it *may* have created the file '/etc/ppp/peers/dsl-provider'. You could try adding the line for the service name at the bottom of that file too. 

I've been doing a fair bit of research on this problem but so far have not found any other obvious solutions.

EDIT:

After looking around some more, I don't think either of those ideas will work. Have a look at the following thread, especially post #8, which provides a line you could add to '/etc/ppp/peers/dsl-provider' which *might* help. It seems getting pppoe to work with the "service name" requirement is a bit tricky.

**Re: PPPoE Issue With Non-Standard Settings Required by ISP**
[http://ubuntuforums.org/showthread.php?t=355377](http://ubuntuforums.org/showthread.php?t=355377)

---

### Post by duvkata on 2007-02-21
thanks for the comments,but none of them helped me.however i figured out the problem by myself i`ll post the solution soon on the same topic

---

### Post by RedSquirrel on 2007-02-23
> **duvkata said:**
> thanks for the comments,but none of them helped me.however i figured out the problem by myself i`ll post the solution soon on the same topic


Please do that. I would like to know your solution (out of curiosity) and I'm sure others will want to know (out of necessity). Thanks. :)

---

