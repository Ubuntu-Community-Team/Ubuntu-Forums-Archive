---
title: "Ubuntu 8.10 (Mozilla Firefox 3.04) and Java"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by pablolie on 2008-12-09
Odd - I have installed and reinstalled Sun's Java library through the Applications Add/Remove menu, and it tells me I have "Sun java 6 Runtime" installed. However, when testing Java in Mozilla Firefox 3.04, and when trying to join a web conference that requires the java plug-in, I am told Java is not installed.

I have noticed that there are 3 plugin folders for Firefox in the following folders under usr/lib

- firefox
- firefox-3.0.4
- firefox-addons
 
And there is a mozilla folder also.

None of them seem to have a Java related entry. Hm, kind of defeats the purpose of the installation via the Applications menu. When looking at Synaptic, it tells me I have 
- sun-java6-bin
- sun-java6-jre
installed. To the ignorant layman it would seem this should suffice. Any help or thoughts, please? I must be able to do the conferencing stuff in Mazilla Firefox, it is a huge business usability limitation if I can't... so any thoughts hugely appreciated.

---

### Post by newbee70 on 2008-12-09
> **pablolie said:**
> Odd - I have installed and reinstalled Sun's Java library through the Applications Add/Remove menu, and it tells me I have "Sun java 6 Runtime" installed. However, when testing Java in Mozilla Firefox 3.04, and when trying to join a web conference that requires the java plug-in, I am told Java is not installed.

I have noticed that there are 3 plugin folders for Firefox in the following folders under usr/lib

- firefox
- firefox-3.0.4
- firefox-addons
 
And there is a mozilla folder also.

None of them seem to have a Java related entry. Hm, kind of defeats the purpose of the installation via the Applications menu. When looking at Synaptic, it tells me I have 
- sun-java6-bin
- sun-java6-jre
installed. To the ignorant layman it would seem this should suffice. Any help or thoughts, please? I must be able to do the conferencing stuff in Mazilla Firefox, it is a huge business usability limitation if I can't... so any thoughts hugely appreciated.



Do you have it disabled in firefox preferences?

edit / preferences / content / java script and or java enable / disable.

---

### Post by pablolie on 2008-12-09
> **newbee70 said:**
> Do you have it disabled in firefox preferences?

edit / preferences / content / java script and or java enable / disable.

Indeed, I have Java enabled there. I also enabled some Java 6.0.2 add-on for Mozilla, and it didn't make a difference. Given the utter absence of Java stuff in the folder I mention above, I suspect something may be broken in the Java installation as of Ubuntu 8.10?

---

### Post by newbee70 on 2008-12-09
> **pablolie said:**
> Indeed, I have Java enabled there. I also enabled some Java 6.0.2 add-on for Mozilla, and it didn't make a difference. Given the utter absence of Java stuff in the folder I mention above, I suspect something may be broken in the Java installation as of Ubuntu 8.10?

Well I just checked my mozilla folder/ firefox, the extensions, and add ons 
it doesn't show up in mine either but java and java script booth work on my system under 8.04.1 

So I will have to pass on this as a possible 8.10 difference.

---

### Post by pablolie on 2008-12-09
> **newbee70 said:**
> Well I just checked my mozilla folder/ firefox, the extensions, and add ons 
it doesn't show up in mine either but java and java script booth work on my system under 8.04.1 

So I will have to pass on this as a possible 8.10 difference.

Thanks for checking. I am now logged in from the Windows Vista partition, where the same visit to install Java 6 yielded different results and the web conference widget works like a charm. Drat...

---

### Post by albinootje on 2008-12-09
For usage in Firefox you need the java-plugin :

sun-java6-plugin

After installing it, and restarting Firefox you can type this in Firefox to check which plugins are detected by Firefox :

about:plugins

---

### Post by albinootje on 2008-12-09
Oops, smileys everywhere..

That should be :
about : plugins (remove the 2 spaces before and after the colon)

---

### Post by newbee70 on 2008-12-09
deleted

---

### Post by denham on 2009-01-14
> **albinootje said:**
> For usage in Firefox you need the java-plugin :

sun-java6-plugin

After installing it, and restarting Firefox you can type this in Firefox to check which plugins are detected by Firefox :

about:plugins

I am having the same problem, I have sun-java6-bin and sun-java6-jre installed, but I don't see a sun-java6-plugin in Synaptic?

---

### Post by kloudy on 2009-01-17
Same problem with me.  I checked the firefox plugins and the plugin mentioned above was not discovered.  I installed the java console in firefox but that made no change either.  I have version 6 installed in Ubuntu via synaptic.

Does anyone else have an idea?

Thanks!

---

### Post by denham on 2009-01-17
I solved it on my system, you need to install Sun Java 6 Update 12 for the 64-bit plugin to be included. Download the RPM, convert it using alien, install it, then create a symbolic link for the plugin in the firefox plugins folder.

---

### Post by kloudy on 2009-01-17
Well folks, I was mistaken and did find the firefox plug-in in the synaptics list.  I installed it along with the 2 java 6.0 releases and now my java is working in firefox.

Continue with a good weekend.

---

### Post by SirAlphonso on 2009-01-21
Hi there,

I have the same problem. I installed the Java 6 Runtime from add/remove programs, then tried doing what the manual said, then tried installing the Java 6.02 plugin from within firefox, but it didn't work.

I found the sun-6-java-plugin package in synaptic, installed it, restarted my computer, but firefox will still not run java applets.

Any advice?

Thanks!

---

### Post by coolzire on 2009-03-06
I have got it working by going in add-on in Firefox (Tool , Add-ons).
Select get add-ons then enter java in the search box. You should see Java Console then choose to add to Firefox. After adding it , Firefox will require a restart.

---

### Post by nexula on 2009-03-11
> **albinootje said:**
> For usage in Firefox you need the java-plugin :

sun-java6-plugin

After installing it, and restarting Firefox you can type this in Firefox to check which plugins are detected by Firefox :

about:plugins

I installed sun-java6-plugin using terminal window:
[INDENT]**sudo apt-get install sun-java6-plugin**[/INDENT]
and everything was working again. :D

---

### Post by homesnake on 2009-04-02
> **nexula said:**
> I installed sun-java6-plugin using terminal window:
[INDENT]**sudo apt-get install sun-java6-plugin**[/INDENT]
and everything was working again. :D

Thanks! I'm a newb and this worked for me, after a restart

---

