---
title: "Can't update java"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by iceman2667 on 2010-09-18
I'm having issues trying to upgrade my ver. of Java. I'm not use to Ubuntu yet so could someone please give me step-by-step commands to install it please? 


thanks

---

### Post by marshmallow1304 on 2010-09-18
First enable the Partner repository.  [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

Using Synaptic or apt-get, install sun-java6-jre.  If you need the browser plugin, make sure sun-java6-plugin is installed.

---

### Post by jtarin on 2010-09-18
> **iceman2667 said:**
> I'm having issues trying to upgrade my ver. of Java. I'm not use to Ubuntu yet so could someone please give me step-by-step commands to install it please? 


thanks
No need if you have Sun Java. It upgrades itself. It will notify you.

---

### Post by claracc on 2010-09-19
Oracle (Sun) Java Runtime Environment (JRE) has been removed from the regular software repositories of Ubuntu 10.04.

So, you can follow this thread tips [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) in order to update your oracle java version

---

### Post by jtarin on 2010-09-19
> **claracc said:**
> Oracle (Sun) Java Runtime Environment (JRE) has been removed from the regular software repositories of Ubuntu 10.04.

So, you can follow this thread tips [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) in order to update your oracle java version
As marshmallow1304 suggest.

```
add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
```
 
This will install sun-java6 packages from Canonical Partner Repository.

Personally I don't see why someone would want to run any other than Sun, but I can understand being faithful to opensource....except when it affects my work.

---

### Post by claracc on 2010-09-19
> As marshmallow1304 suggest.

Code:

add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

 Personally I don't see why someone would want to run any other than Sun, but I can understand being faithful to opensource....except when it affects my work. 

Personally what I don't understand is your comment. Perhaps you only have read the very begining of the thread [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java), in it there are various approaches to have java in linux ( included the propossed by marshmallow1304).

To add more information about a problem it is always good, in this way  people is better prepared to do a good election.

And to solve problems there is always more ways than "the way I have said".

Regards

---

### Post by jtarin on 2010-09-19
> **claracc said:**
> Personally what I don't understand is your comment. Perhaps you only have read the very begining of the thread [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java), in it there are various approaches to have java in linux ( included the propossed by marshmallow1304).

To add more information about a problem it is always good, in this way  people is better prepared to do a good election.

And to solve problems there is always more ways than "the way I have said".

RegardsIf you don't understand my comment why don't you ask for clarification instead of getting on a soapbox. I know very well all the approaches to installing Java I don't need you to hand me a link.....those are everywhere. Better yet why didn't you just explain your position when you posted instead of attacking mine....which I might add...I never said it was the only way for everybody.Follow your own advice.> And to solve problems there is always more ways than "the way I have said".

---

### Post by jtarin on 2010-09-19
> **claracc said:**
> Personally what I don't understand is your comment. Perhaps you only have read the very begining of the thread [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java), in it there are various approaches to have java in linux ( included the propossed by marshmallow1304).
Your link is "ALL" about Sun Java with bare mention of two others....so what are you going on about.
Regards.:P

---

