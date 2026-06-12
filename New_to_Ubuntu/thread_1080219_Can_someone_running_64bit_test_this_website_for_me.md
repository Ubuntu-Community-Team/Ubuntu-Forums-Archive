---
title: "Can someone running 64bit test this website for me."
date: 2009-02-25
forum: New to Ubuntu
---

### Post by philinux on 2009-02-25
Reinstalled intrepid and went for 64 bit. All well apart from this website.

[http://www.thinkbroadband.com/speedtest.html](http://www.thinkbroadband.com/speedtest.html)

When i run the speedtest. I have to keep refreshing the page to get the applet to run. But eventually once run it returns this.
[http://speedtest1.thinkbroadband.com:81/0%9B%B9%F4%B6%7F](http://speedtest1.thinkbroadband.com:81/0%9B%B9%F4%B6%7F)

Instead it should display a results page. It worked on 32 bit. I've contacted the website they say it works fine. They replied.
> Hi Phil,

I've just run the test and it appears to work fine. I'm not quite sure why you would get the URL you've pasted from there--This would suggest something on your computer is altering the URL before it is seen by our server. We're seeing you request something very odd:

/L%19%B01%7F

I would suggest you try another web browser and see if the problem persists.

So tried creating a new FF profile and running epiphany with same result.

---

### Post by handy on 2009-02-25
Well, I can run your speed tests from the site, though I am using Arch 64bit.

I get this page at the end:

*_[http://www.thinkbroadband.com/speedtestcomplete.html?id=123556739058679811801](http://www.thinkbroadband.com/speedtestcomplete.html?id=123556739058679811801)_*

Which hopefully you can see, as I got a 404 on your second link?

---

### Post by howefield on 2009-02-25
Working fine on 64 bit Ubuntu.

---

### Post by philinux on 2009-02-25
Thanks for replies.

Still getting 404 error here and the applet is a pain to get to start.

This is a clean install too running icedtea java. This website at least worked in 32 bit. I need this to work as my isp insists on it being used when complaining about speed and I have a profile going back over the last 12 months of my speed results.

---

### Post by howefield on 2009-02-25
> **philinux said:**
> This is a clean install too running icedtea java.

As I say, it works for me, but I am not using icedtea. Don't know if that is the difference.

---

### Post by handy on 2009-02-25
If you haven't found other problems with regard to surfing the net, I'd apply pressure on the ISP.

Really, they should find a more all encompassing site to do what they require for their valued customers.

---

### Post by avtolle on 2009-02-25
Phil, hazarding a guess here; the applet needs Sun's java to run. There is a 64-bit plugin for this, but I'm not on my 64-bit system right now and I cannot recall if one installs it from the repos or just what. Take a look at the 64-bit users forum, IIRC there is a sticky on installing 64-bit Java there. Good luck.

---

### Post by LowSky on 2009-02-25
Hi Phil, I know you might have done this but its worth a shot

Run this command from terminal, it will install JAVA, Flash, MP3 supprt, MSTcorefonts, and maybe something else.
```
sudo apt-get install ubuntu-restricted-extras
```

then reboot

then try running your test again

---

### Post by sydbat on 2009-02-25
I may have figured out the problem for you philinux.

I went to the linked site and it wanted me to download Java. Strange, I thought, because I was sure I had it installed. I checked and sure enough, it is.

So I wondered why it didn't want to work for online things (I checked around and could not use Java specific website items on other sites). So I went back to your first link and clicked on the Java icon, which opened a frame (UGH) that was the Sun site in miniature.

In that frame it has a button to download the "latest Java" and I clicked it. The next mini-page had download options, and I had to scroll to the right to find the "check if Java is installed" (or whatever it said) option. I clicked it and Firefox told me I was missing plugins. Hmmm...

So I chose to install missing plugins and was given 2 options "GCJ" and "GCJ open" (not the exact wording, but you get the idea). I figured the first one, being from Sun would work, chose it, let it install, restarted FF, and...nothing.

So I redid the above steps, got the "missing..." prompt again, chose the second option, and...voila! The site now renders correctly and I can use the Java-based speed test.

As an aside, I go to [dslreports]("http://www.dslreports.com/speedtest") to test speed and was unable to do the Java-based test before. Now it works fine.

I hope this helps.

---

### Post by philinux on 2009-02-25
Thanks sydbat I download the file jre-6u12-linux-x64.bin and howefield in the 64 bit forum provided these instructions.
> 
Remove all current java files you might have by :

sudo su
apt-get -y purge icedtea6-plugin
rm -f /usr/lib/firefox-addons/plugins/libnpjp2.so
rm -f /usr/lib/firefox-addons/plugins/libjavaplugin_oji.so
rm -f /usr/lib/mozilla/plugins/libnpjp2.so
rm -f /usr/lib/mozilla/plugins/libjavaplugin_oji.so

Download the latest version of java RE here. move it to to /opt and install:

mv ~/Desktop/jre-6u12-linux-x64.bin /opt/
cd /opt/
sh jre-6u12-linux-x64.bin

after installing link the plugin to your firefox plugin directory.

cd /usr/lib/mozilla/plugins
ln -s /opt/jre1.6.0_12/lib/amd64/libnpjp2.so 

All good now.

---

### Post by Kellemora on 2009-02-25
Hi Phil

You're VERY LUCKY!

I've tried those exact same instructions, and they never worked for me.

Also tried the ones on the Java website, those didn't work either.

The Java website keeps saying OOPS you have the wrong version!

There is NOTHING In /opt/ EXCEPT that version and the files IT created!

Strange, hi hi..........

Since you cannot cut n paste into /opt/ it took like 11 tries in Terminal before the file finally moved from the Desktop to the /opt/ directory.

I have to type the FULL PATH NAME, the Tilde has NEVER worked on anything I have ever tried it on yet!

OH, I can't see your web site either!

TTUL
Gary

---

### Post by halovivek on 2009-02-26
Please install the ubuntu extras. it will work fine. i got the same error. once i have installed the ubuntu extras as well as the proprieties to the ubuntu. it is doing fine. i am using UBUNTU 64 bit only.

---

### Post by Kellemora on 2009-02-26
If you're talking about Ubuntu Restricted Extra's, that's one of the first things I install when setting up a new computer.

In fact, there are like 18 things I have to install or change on a new install, just to make sure most things do work right.

But it's sorta over the dam now, the new update that came down the pike this morning killed three of our most used computers.

Right now I'm trying to find out how to undo the DAMAGE this mornings update created here so we can get some work done.

I didn't let the updates download until I tested it on a test computer, worked great there, so I let it download and install on all the rest during lunch hour.  I don't know when I'm going to learn to wait until after closing on Friday Night to let upgrades down load?  Every time I don't, I have serious problems that shoots a day of work all to H.

TTUL
Gary

---

