---
title: "Straw does not update, shows errors in terminal"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2009-04-28
I recently updated my EeePC901 to Jaunty in a clean install and despite some bumps along the way have been mostly happy with the way things have gone.  Since my installation though I have been unable to update my feeds in Straw.  Running it from terminal gives off these error messages:

```
bornagainpenguin@EeePC901:~$ straw
/home/bornagainpenguin/.themes/Human Compact/gtk-2.0/gtkrc:100: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/bornagainpenguin/.themes/Human Compact/gtk-2.0/gtkrc:101: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/bornagainpenguin/.themes/Human Compact/gtk-2.0/gtkrc:116: Murrine configuration option "style" is not supported and will be ignored.
/home/bornagainpenguin/.themes/Human Compact/gtk-2.0/gtkrc:156: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/bornagainpenguin/.themes/Human Compact/gtk-2.0/gtkrc:229: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
strawdbus.py:69:start_services: Error while connecting to NetworkManager: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 7 matched rules; type="method_call", sender=":1.75" (uid=1000 pid=5088 comm="/usr/bin/python /usr/bin/straw ") interface="(unset)" member="state" error name="(unset)" requested_reply=0 destination=":1.10" (uid=0 pid=2848 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
```

Can anyone suggest some fixes for me?

NOTE: Please do not use this thread to pull for your RSS\Feed Reader of choice, I stick with Straw because it is the only *true* offline reader that exists in Linux--one that grabs images as well as text and allows them to be read offline.  Since my EeePC is intended to be portable and I am not always able to find an open WiFi connection, I need to be able to read things offline and Straw lets me do that.  Or it did up until I installed Jaunty anyway...

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-04-28
I'm going to back up my system and restore my Acronis image of Intrepid, since no one seems to know what is happening here and I have not been able to find anything in Google to help me fix it myself.  I can only assume this is a new issue having to do with either the network manager or the python upgrades.  Possibly both.

I will still keep an eye on this thread in case someone is able to figure out the issues, then I'll move back to Jaunty.  Until then I get better performance and my killer app Straw simply works in the older versions of Ubuntu.

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-05-07
/bump

---

### Post by bornagainpenguin on 2009-05-15
/BUMPS again...

---

### Post by bornagainpenguin on 2009-05-20
You know...it's been three weeks now and no one has even bothered to post in this thread besides myself.  People are always saying how much they hate it when someone bumps a thread several times a day or goes on a rant and threatens to leave when they don't get the solution they need right away.  I despise that kind of thing myself, because I consider it emotional blackmail, but...here I am some three weeks later.  No answers, not even a quick post with someone commiserating or promising to give it a look and see if they can figure it our.  Nothing.

Is it any wonder people resort to the tactics mentioned above, when trying to do things the right way yields no results?

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-06-12
Six weeks.  Does anyone have any ideas on how to fix my problem?  Not asking about the theme errors, needing help getting Straw to work!

Thank you.

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-06-14
/bump

---

### Post by bornagainpenguin on 2009-06-14
I recently reinstalled Jaunty and am loving it with the exception of not having my straw feed reader working.

```
strawdbus.py:69:start_services: Error while connecting to NetworkManager: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 7 matched rules; type="method_call", sender=":1.61" (uid=1000 pid=5778 comm="/usr/bin/python /usr/bin/straw ") interface="(unset)" member="state" error name="(unset)" requested_reply=0 destination=":1.11" (uid=0 pid=2879 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
```

The above is the error message seen in the terminal when I start the program.

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-06-15
Started a new thread, linked here: [http://ubuntuforums.org/showthread.php?t=1186595](http://ubuntuforums.org/showthread.php?t=1186595)

I'm hoping that by having two threads open I can increase my chances of getting an answer from **someone**!

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-06-15
/BUMPing because no one cares

---

### Post by bornagainpenguin on 2009-06-16
IS ANYONE ONE THERE????

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-06-17
Bump

---

### Post by bornagainpenguin on 2009-06-19
/daily bump

---

### Post by bornagainpenguin on 2009-07-02
/Still interested bump

---

### Post by bornagainpenguin on 2009-07-28
/bump

---

### Post by bornagainpenguin on 2009-08-05
/Bump to show that I care.  We all need a little more bumping in our lives.  Perhaps if...

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-10-20
/forlorn bumpage here.

---

### Post by bornagainpenguin on 2009-10-29
Hope springs eternal /BUMP

---

### Post by bornagainpenguin on 2010-07-26
A)  This issue can be fixed by removing the python-adns package, which despite having Straw claim in the terminal does NOT help speed things along, but rather breaks the application.

B)  I am now using [Naufrago!]("http://www.gnomefiles.com/app.php/Naufrago!") for my ofrfline feed reading.

--bornagainpenguin

---

