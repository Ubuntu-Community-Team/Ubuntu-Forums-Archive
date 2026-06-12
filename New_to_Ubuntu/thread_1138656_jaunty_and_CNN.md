---
title: "jaunty and CNN"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by DarinB on 2009-04-26
i thought i had juanty finally running with all the hulu issues but now i noticed that cnn stream video dosen't work
msnbc does and hulu and you tube

---

### Post by MontelEdwards on 2009-05-06
> **DarinB said:**
> i thought i had juanty finally running with all the hulu issues but now i noticed that cnn stream video dosen't work
msnbc does and hulu and you tube
Chances are that the site was down.
Sometimes sites just gotta do a little matience, or whatever. 
Or there may be something wrong with their flash program, or whateverr.
So as long as you can watch YouTube you should be coool ;)

---

### Post by acimmarusti on 2009-05-06
Use this in a terminal:

```

sudo apt-get install ubuntu-restricted-extras

```

cheers

---

### Post by MontelEdwards on 2009-05-06
restriced extras dosent come with the JRE plugin... i dont think

---

### Post by acimmarusti on 2009-05-06
yes it does. There is proof here:

intrepid: [http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)
jaunty: [http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras)

---

### Post by MontelEdwards on 2009-05-06
lol.
no,
it doesnt.
It installs JRE, yes.
Not the sun-java plugin.
it comes with the IceTea, which he/she has

---

### Post by acimmarusti on 2009-05-06
That's weird. The intrepid package does include it!, but not the jaunty one. Well, he/she can install it as well

---

### Post by presence1960 on 2009-05-06
if you're using 64 bit Ubuntu, follow this to add java plug in : [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

for 64 bit Flash : [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

uninstall other Flash prior to installing another Flash version.

This is what you will get for java plug in:
```
raz@raz-desktop:~$ java -version
java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b01)
OpenJDK 64-Bit Server VM (build 14.0-b10, mixed mode)
raz@raz-desktop:~$ 
```

Just want to acknowledge zika for the how to.

---

### Post by DarinB on 2009-05-28
you wouldn't believe this,,,,about three weeks ago i was suggested to add flash block to make cnn video work. but looking back at the post i saw that someone added remove ad block which i do not have that add on, so i tried removing flash block and I'll be a monkeys uncle i have cnn video now!!!!!!!!!!!!!
i did like flash block for things like hulu but no big deal if i run into other problems i will be back
thanks all even weeks later fixes can get resolved!!!!!

---

### Post by Trapper on 2009-06-10
Just my experience:

I have Adblock Plus 1.0.2 with firefox 3+ and Adobe flash. I've found in U9.04 and U9.10 that the only way I can view videos at cnn.com/video is to make cnn.com an exclusion in my ad blocking list. YouTube and other sites I use seem to work okay without making adjustments to Adblocker Plus.

---

### Post by entropy1 on 2009-08-09
Thank you!  I've been trying to solve this problem for several months.  By adding cnn.com to the whitelist in the preferences of flashblock, I get cnn video now.

---

