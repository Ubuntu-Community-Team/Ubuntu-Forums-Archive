---
title: "Orange Livebox, does anyone know how to make it work?"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Rhapsody on 2008-04-29
This is a fairly long-standing problem that I suspect will be relatively simple to fix, so I want to get it over and done with now.

The hardware is an [Orange Livebox 1.1](http://en.wikipedia.org/wiki/Orange_Livebox), a fair generic piece of UK ADSL hardware. What I really need to do with it is fairly simple, I want to connect it to my main PC via the ethernet cable (using an ethernet port on my PC's motherboard, which Kubuntu seems to have detected) and use it to access the internet.

The problem with this is that while Kubuntu seems to see the ethernet port, I've been given no solid indication that it can actually detect the Livebox itself, and I need to authenticate with my username and password before I can go online, which will require that Kubuntu starts talking to it.

I seem to be able to find some discussion about it, but they all entail GUI tools on Ubuntu, using applications that aren't present in Kubuntu. So what is the KDE way to make a wired router work?

---

### Post by Rhapsody on 2008-04-30
I'm afraid I'm going to have to bump this. I'm frustrated and angry. I've had no help whatsoever on this problem. It can't be a rare or complex one, it's just something where I lack knowledge and I'm been left feeling completely isolated. What am I supposed to do with this thing? How do I make it work? What am I missing?

---

### Post by natrixgli on 2008-04-30
Just a shot in the dark, but KDE has a GUI for PPP called, oddly enough, KPPP. Maybe that will help?

Cheerio,

-n8

---

### Post by Chainz on 2008-04-30
Take a look at this one: 
[ubuneo.ubuntu.pl]("ubuneo.ubuntu.pl")
I believe it would be perfect.

You can also try:
[http://forum.fedora.pl/index.php?showtopic=11290]("http://forum.fedora.pl/index.php?showtopic=11290")
Might be handy :)

But just between you and me. Just type: ubuntu neostrada livebox in Google and you will get lots of information ;)

---

### Post by Rhapsody on 2008-04-30
Well then, status update.

I looked around on the forums and found suggestions for a web-based configuration through 192.168.1.1, which didn't work. It seemed to detect my router, asked for a username and password, but didn't accept the (perfectly valid) ones I gave.

KNetworkManager gives me some hope, as it definitely detected the Livebox, but gave me no ways to login and didn't actually give internet access.

KPPP seems dedicated to dial-up services (hence the fact that it allows you to specify serial ports as input), but I use ADSL. That seems to be a bust.

As for UbuNeo, I really don't know whether to laugh or cry. My last hope for getting my Livebox working is a generic source code package with the instructions in **Polish**? I don't even know if it would solve my problems, as I have absolutely no way of reading the pages its on. Is this what Linux for Human Beings is about?

---

### Post by natrixgli on 2008-04-30
Hrm. I thought KPPP would be more like Gnome-PPP.

Gnome-PPP has an ADSL option where it will only require a username/password, no number. Even though you use KDE, you can still install Gnome-PPP. 


Cheers,

-n8

---

### Post by jetsam on 2008-04-30
> I looked around on the forums and found suggestions for a web-based configuration through 192.168.1.1, which didn't work. It seemed to detect my router, asked for a username and password, but didn't accept the (perfectly valid) ones I gave.

Try **admin** and **admin** for the username and password.  See step 3 here:
[http://help.orange.co.uk/documentDisplay.do?resultType=5002&docProp=$solution_id&groupId=1&directSolutionLink=3&gotoLink=0&page=&clusterName=DefaultCluster&docType=1006&docPropValue=kb14497]("http://help.orange.co.uk/documentDisplay.do?resultType=5002&docProp=$solution_id&groupId=1&directSolutionLink=3&gotoLink=0&page=&clusterName=DefaultCluster&docType=1006&docPropValue=kb14497")

In theory, you then enter your real username and password provided by your ISP under Configuration Homepage-->My services-->Internet.

I've never used a livebox, but my impression when I looked into it last time I tried to help with one on the forum was that, once you get the livebox authenticated with your service, it acts like a fairly standard router if you're using a wired connection.  

That you're communicating with the livebox at all indicates that your Ubuntu-->Livebox connection is fine, and the only problem now is the Livebox-->ISP connection.

---

### Post by ushills on 2008-04-30
I have a livebox used in the uk and the correct setup routine is to go to 

[http://192.168.1.1](http://192.168.1.1)

and use the user name admin and password admin.

Just confirmation that the previous post was correct.  I never had to enter another password or anything to connect to the orange service, if you are using with another ISP then google for the orange livebox forum they are fairly active and have helped me before.

If you need help with reconfiguring the box to use the Orange ISP there is a reset option through the web interface that restores to factory settings.

---

### Post by Rhapsody on 2008-05-01
> **jetsam said:**
> Try **admin** and **admin** for the username and password.  See step 3 here:
[http://help.orange.co.uk/documentDisplay.do?resultType=5002&docProp=$solution_id&groupId=1&directSolutionLink=3&gotoLink=0&page=&clusterName=DefaultCluster&docType=1006&docPropValue=kb14497]("http://help.orange.co.uk/documentDisplay.do?resultType=5002&docProp=$solution_id&groupId=1&directSolutionLink=3&gotoLink=0&page=&clusterName=DefaultCluster&docType=1006&docPropValue=kb14497")

In theory, you then enter your real username and password provided by your ISP under Configuration Homepage-->My services-->Internet.
This worked, thank you everyone.

---

