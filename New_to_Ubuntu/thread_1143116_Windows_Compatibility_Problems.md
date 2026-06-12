---
title: "Windows Compatibility Problems"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by roveriver on 2009-04-29
Wondering if anyone out there can help me out.  I have just recently downloaded Wine and don't know anything about it or how it works.  I have several programs that I'd like to download onto my laptap, but can't even get them to run.  Do you have to have something already installed before you use Wine?  Thanks

---

### Post by kanikilu on 2009-04-29
What programs are you trying to use?

Check out the AppDB over at WineHQ to see if anyone else is successfully using the same programs under Wine:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by aufan19 on 2009-04-29
Not all Windows programs will run under Wine. Some run perfectly, others need tweaking, and some don't run at all. As far as getting them to open under Wine, I think you right-click and choose "open with Wine". Like kanikilu said, you should check the AppDB. If it turns out that they don't work, there might be OSS that can complete the same task. What programs are you using?

All you have to do to install wine is type "sudo apt-get install wine" (without the quotes). I'm not aware of anything else you would need to install.

---

### Post by NightwishFan on 2009-04-29
Press alt+f2 and type:

```

winecfg

```

You can configure Wine there. After you do this, simply click on a Win32 .exe file to run it like in Windows. Many games/programs work.

I advise you try a newer version of Wine if your program almost works, but it buggy. To get an upstream version of Wine, go to:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Follow the instructions there.

Also remember to look for your app in the WineDB like the above poster said.

---

### Post by lovinglinux on 2009-04-29
It seems that you are trying to run every program you used before on Windows. This is not the best approach. Wine can be useful when you can't find a Linux alternative for your favorite application, but you shouldn't install only Windows programs on your Ubuntu machine. Wine is not perfect.

There hundreds of programs in the repositories that are native to Linux and  optimized to be used on Ubuntu. Additionally, lot's of them are better than Windows counterparts. So if you could tell which programs you want to install, maybe we could recommend the Linux alternative for you.

---

### Post by NightwishFan on 2009-04-30
I agree, there are many full featured Linux alternative applications. The only things you might need Windows programs for are video editors and modern games. Linux has games too, try out frozen-bubble, battle for wesnoth, and urban terror.

---

### Post by Mark Phelps on 2009-04-30
Heartily agree with Lovinglinux. 

Wine is useful if (1) you absolutely must run an MS Windows app because there's no reasonable alternative in Linux, (2) you've made a major investment in MS Windows apps files that simply can't be used in Linux, and (3) the "rating" in Wine for that app is Gold or better.

I've read reports that the commercial version (Crossover) is MUCH better at running a wider variety of MS Windows apps -- but you'd have to buy it to find out.  And if it did not work better for your particular MS Windows apps, you've wasted your money.

So basically, if you've come to Linux primarily to reuse your MS Windows apps, you're most probably going to be severely disappointed and frustrated by the results.

---

