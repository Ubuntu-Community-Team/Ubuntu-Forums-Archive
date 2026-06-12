---
title: "Befuddles &amp; pretty angry JRE / no JRE CRAP"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-12-18
The question is at the bottom. Thanks.

Every time I have gone to the [Sun JAVA site]("http://www.java.com"), and downloaded their stupid software, I get nothing but 

"Verifying Java Version
Oops! You don't have the recommended Java installed."

So, today, like a fool, I again d/l this "software". Then I netsearched: 

how to install binary ubuntu

that took me to:
[URL="http://ubuntuforums.org/showthread.php?t=233309"]
How do I install a .bin file?[/URL]

There, I did

chmod a+x jre-6u17-linux-i586.bin

the terminal spun out the license, I kept pressing the space bar and at the end of the license, I was asked to type the letter "y" to accept. I accepted, the terminal ran more code and the install ended reporting NO errors. So I closed the browser, warm-booted, went back to the Java page above and found IT cannot find it's own JRE Q#$ FQ#$ $T (I'm so angry). So, reading about .bin some more, I tried to ./ without the sudo. The license came up, I clicked Y and the installer asked to R(eplace) and I clicked that or (O)verwrite. Any way, another warm boot and the insane Java page still says I don't have their friggin' software!!!

Why? And can this be fixed in 30 minutes or less?

---

### Post by halitech on 2009-12-18
Certainly it can in (hopefully) under 5 minutes

open a terminal and run
```
sudo apt-get install xubuntu-restricted-extras
```
this will install the apps listed here: [http://ubuntu-tutorials.com/2007/08/17/ubuntu-restricted-extras-all-that-extra-stuff-all-in-one-place/](http://ubuntu-tutorials.com/2007/08/17/ubuntu-restricted-extras-all-that-extra-stuff-all-in-one-place/)

---

### Post by mgmiller on 2009-12-18
```
sudo apt-get install xubuntu-restricted-extras
```only works if he is running xubuntu.  If he is running ubuntu, the command should be:

```
sudo apt-get install ubuntu-restricted-extras
```and if he is running kubuntu it would be:

```
sudo apt-get install kubuntu-restricted-extras
```

That being said, the restricted extras package doesn't always pull in java.

The 3 packages of most interest are:

sun-java6-bin
sun-java6-jre
sun-java6-plugin

They are easily added in synaptic or by:

```
sudo apt-get install package-name
```
where package-name is one of the 3 sun-java packages I listed above.

---

### Post by halitech on 2009-12-18
> [xubuntu] Befuddles & pretty angry JRE / no JRE CRAP

I took from the fact that the OP used the xubuntu prefix to indicate they were running Xubuntu so that is why I only gave the command for xubuntu as the others wouldn't be relevant for them.

---

### Post by mgmiller on 2009-12-18
When all else fails, read the instructions.....
I didn't catch the [xubuntu] in the title....](*,)

I guess my post could help out any flavor of 'buntu.

Have you noticed that the restricted extras package doesn't always pull in java?  Don't know why it does that.

---

### Post by halitech on 2009-12-20
I usually scan for the Xubuntu ones as I'm running XFCE so I can usually help out there a little better then the Ubuntu ones if its XFCE specific :D

Never noticed that it doesn't always pull in java, might be a glich if the repo is acting up or something.

---

### Post by jamesstansell on 2009-12-21
> **mgmiller said:**
> 
Have you noticed that the restricted extras package doesn't always pull in java?  Don't know why it does that.

I haven't seen that myself, but 2 guesses about when it could happen.

1) before sun-java6 update 12 (or maybe 14?) there was no sun-java for 64-bit Linux, so restricted extras for 64-bit wouldn't have been able to include sun-java

2) starting with Karmic (ubuntu 9.10) sun-java is orphaned, which effectively means it's not being updated regularly, not even for security fixes.  It would surprise me if was removed from restricted extras because of that but I'm not running 9.10 yet and I haven't investigated thoroughly.

OK, 3rd guess: sun-java6 for Linux isn't available for non-intel architectures, so for ppc, arm and others that's another case where restricted extras couldn't include it.

Regards,

-james.

---

### Post by mgmiller on 2009-12-21
> 2) starting with Karmic (ubuntu 9.04) sun-java is orphaned, which effectively means it's not being updated regularly, not even for security fixes.

Karmic is 9.10.

Sun-java is orphaned?  What has replace it?

---

### Post by Mighty_Joe on 2009-12-21
> **mgmiller said:**
> Sun-java is orphaned?  What has replace it?

[OpenJDK]("http://openjdk.java.net/")
[This bug]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426") has some discussion as to the logic behind the decision.

---

### Post by jamesstansell on 2009-12-21
> **mgmiller said:**
> Karmic is 9.10.
Thanks! (I must have been in too much of a hurry last night.)

> **mgmiller said:**
> Sun-java is orphaned?  What has replace it?

openjdk6. It became the default java in ubuntu around 8.10.  [http://blogs.sun.com/barton808/entry/openjdk_default_java_runtime_in](http://blogs.sun.com/barton808/entry/openjdk_default_java_runtime_in)

But sun-java6 wasn't orphaned until a few months ago.  The announcement can be found somewhere in the debian bugtracker.  I haven't heard any discussion so far from anyone interested in becoming the new maintainer.

But since the sun-java browser plugins are still important, I really hope that the package doesn't remain unmaintained for much longer.

Regards,

-james.

---

### Post by mgmiller on 2009-12-21
Here is some more info I found on this topic:
[http://blogs.sun.com/darcy/entry/openjdk_and_the_new_plugin](http://blogs.sun.com/darcy/entry/openjdk_and_the_new_plugin)


So it would appear, the packages to install now are:
default-jre
icedtea6-plugin

The default-jre says it will point to the 64 bit versions as needed.

I think these 2 will pull in all the other needed packages.

I haven't tried this yet, as I am still using the sun-java6 packages and they seem to work everywhere I need them to.

As I stated earlier, I installed ubuntu-restricted-extras on a clean install of karmic 64 bit and none of the open jdk packages were installed.  I went back and did the 3 sun-java6 packages as I always used to.  I also have 2 32 bit clean installs of Karmic, both of which have restricted-extras installed and in both of those cases I had to install sun-java6 as well.  No openjdk was found.

---

