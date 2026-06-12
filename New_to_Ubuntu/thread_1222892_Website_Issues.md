---
title: "Website Issues"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by ketedford on 2009-07-25
Now that I have been running Ubuntu 9.04 for about three weeks, I am having a few issues with websites that I visit. 

1) When I post something on a local site, syracuse.com, I get an error:

**Movable Type**

      **An error occurred**

  There was an error writing to the log file: Permission denied at /var/www/cgi-bin/mte/plugins/LogToDisk/LogToDisk.pl line 117. 


2) When signing on to mycokerewards.com, it never connects. The icon just spins for as long as I stay on the page. 

Any ideas? Any help would be greatly appreciated.

---

### Post by halitech on 2009-07-25
for #1, thats an issue with the server at syracuse.com, not much you can do about it but let the webmaster know about the issue and hope they fix it.

---

### Post by ketedford on 2009-07-25
For #1, is it an error on the server not allowing non-windows to post?

---

### Post by wojox on 2009-07-25
#2 Try this link: [http://www.mycokerewards.com/home.do](http://www.mycokerewards.com/home.do)

---

### Post by halitech on 2009-07-25
> **ketedford said:**
> For #1, is it an error on the server not allowing non-windows to post?

if they are that pro-MS/anti-everything else, then I guess they could have written the code to not allow non-windows users to post but I doubt that, more likely just bad coding

---

### Post by ketedford on 2009-07-25
That link to coke does not work. :-(

---

### Post by halitech on 2009-07-25
> **ketedford said:**
> That link to coke does not work. :-(

the link worked for me, do you have java enabled or noscript installed in firefox?

---

### Post by ketedford on 2009-07-25
:confused: How would I find that out?

---

### Post by halitech on 2009-07-25
tools - addons in firefox will tell you whats installed there.

---

### Post by ketedford on 2009-07-25
I don't appear to have either. Can you tell me how to install?
Actually, I do have Java enabled.

---

### Post by halitech on 2009-07-25
no-script will block java so you don't want it installed. which java do you have installed?

---

### Post by QIII on 2009-07-25
You may have Java enabled on your browser, but you may not have Java installed.

You can install the open source version of Java, but there are nefarious agents in the world who spurn anything form the open source community and will turn you away from the door.

Use the terminal as follows to be sure that you have Sun Java:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts sun-java6-jdk
```

You may leave off the fonts and jdk, if you care to.

Then, make sure that the Sun Java will be the preferred alternative:

```
sudo update-java-alternatives -s java-6-sun
```

Finally, check to  see what version you are running:

```
java -version
```

Depending on your architecture and OS, you should get something that looks like this:

```
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)
```

---

### Post by ketedford on 2009-07-25
Just did the java install as outlined in the previous post. My version is:


eric@eric-laptop:~$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Client VM (build 14.0-b16, mixed mode, sharing)
eric@eric-laptop:~$ 


I uninstalled the noscripts and I still can not log in to the mycokerewards.com site. I also put in the wrong password to see if it would kick to another screen showing me that it did read it, however it does the same and just keeps spinning and attempting to log in without actually doing it. 

The one reply says that he can log in. What could possibly be wrong on my part?:confused:

---

### Post by QIII on 2009-07-25
Could you try again and take a look at the lower left-hand corner of the FF frame and give me an idea what text you see down there?

---

### Post by stalkier on 2009-07-25
Coke Rewards works on my side. I know this doesn't help. Sorry.

---

### Post by ketedford on 2009-07-25
When I hover on the button, I see Javascript: void (0)
Clicking on it then gives me a spinning bottle and continues until I just finally close the screen. :(

---

### Post by QIII on 2009-07-25
OK.  I've seen that in the past, particularly on secure sites.

Happened to me just this afternoon after I signed on to my VFW account and attempted to make a donation with a credit card.

If it's any comfort, I ran into the same problem on a Windoze machine with FF.  I eventually had to use Exploder.

There are several posts dealing with "faking out" websites by letting FF make them think it is Exploder by using user agent spoofing.

I'll poke around and maybe we can both find the solution to our problems.

---

### Post by ketedford on 2009-07-25
Thanks. It is driving me nuts.

---

### Post by QIII on 2009-07-25
It could be that the designers of Coke's web site are either IE snobs or they just didn't code it for FF.

Open FF and go to Tools | Add-ons and search for

"User agent switcher"

Install it.

Under tools you will have a new selection "Default user agent".

You can use that to toggle between user agents.

Try your Coke site again and let me know if that helps.  If not, I guess we'll have to look at something else...  I don't know what that might be right now!

---

### Post by ketedford on 2009-07-25
Nope. :-( I'll get back in to it tomorrow morning. Thanks for trying, I appreciate it.

---

