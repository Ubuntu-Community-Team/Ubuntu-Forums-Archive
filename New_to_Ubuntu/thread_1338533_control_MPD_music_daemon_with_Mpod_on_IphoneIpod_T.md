---
title: "control MPD music daemon with Mpod on Iphone/Ipod Touch"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by Harry789 on 2009-11-26
I have a fully working MPD server on my desktop. GMPC as client works flawlessly.

I came across this

[http://www.katoemba.net/makesnosenseatall/mpod/](http://www.katoemba.net/makesnosenseatall/mpod/)

and think it is fabulous - but I have no idea on how to setup the darn thing.

Got MPod downloaded to my ipod touch and can enter the application on ipod, but how do I setup connection so I can remote control music on my desktop?

thanx!

---

### Post by spirion on 2009-11-26
Try this:

1) Open a Terminal

2) Enter this command to back up your MPD configuration file in case you need to go back to it:

sudo cp /etc/mpd.conf /etc/mpd.conf.bak

3) Now enter this command to edit the text configuration file:

sudo gedit /etc/mpd.conf

4) Find the line that says (was line number 69 in mine):

bind_to_address                "localhost"

5) Add a # symbol at the beginning of the line to comment it out. Should look like this:

#bind_to_address                "localhost"

6) Save the file. 

7) Go back to the terminal enter this command to restart the MPD server:

sudo /etc/init.d/mpd restart

That did it for me. Good luck!

---

### Post by Harry789 on 2009-11-26
Thanx, will try.

What I am more specifically looking for is how to setup MPoD once running on the Ipod touch.

It says "new connection" where I can enter 
name
server

what do I enter in those fields to make the MPoD connect? What did you enter since it worked for you?

---

### Post by Harry789 on 2009-11-26
Tried your suggestion.

It does change MPods behavior so we must do something right.

Now MPod start loading the database but then it suddenly quits the application.

I retry but it keeps exiting the MPoD application as soon as it begins to load database (5000 songs)

---

### Post by spirion on 2009-11-26
On mine it's:

Name: [whatever you want to call it]

Connection Mode: Remote

Server: 192.168.1.100 [yours will be different, just whatever the local IP of your machine is]

Port: 6600

Password: [optional, has to be enabled in the mpd.conf file first]

Load Songs: Yes [I wonder if setting this to "No" will stop yours from crashing]

FHEM: Don't Use



> **Harry789 said:**
> Thanx, will try.

What I am more specifically looking for is how to setup MPoD once running on the Ipod touch.

It says "new connection" where I can enter 
name
server

what do I enter in those fields to make the MPoD connect? What did you enter since it worked for you?

---

### Post by Harry789 on 2009-11-28
Thanx, and for the complete noobie question: How do I find the local IP of my machine?

---

