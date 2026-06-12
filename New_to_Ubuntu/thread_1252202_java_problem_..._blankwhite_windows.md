---
title: "java problem ... blank/white windows"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by crowhill on 2009-08-28
hi there

i've got the 9.04 ubuntu version running on a rather new dell desktop pc.

i installed the sun's java packages so that now i have the version 1.6.0_14-b08.

when i open java applications such as maple (12 or 13) or the jin chess software i get a blank/white window without any content. if i resize the window the content suddenly appears. 

is there a fix to this problem? i looked at [http://74.125.93.132/search?q=cache:vpN7-oleqkMJ:https://launchpad.net/bugs/89189+linux+ubuntu+java+applications+blank+white+window+screen&cd=6&hl=en&ct=clnk&gl=ca&client=firefox-a](http://74.125.93.132/search?q=cache:vpN7-oleqkMJ:https://launchpad.net/bugs/89189+linux+ubuntu+java+applications+blank+white+window+screen&cd=6&hl=en&ct=clnk&gl=ca&client=firefox-a) and [https://bugs.launchpad.net/ubuntu/+bug/152040](https://bugs.launchpad.net/ubuntu/+bug/152040) but that didn't really help.

does (or did) anybody experience the same/a similar problem?

some hints would be awesome.

thanks a lot in advance,
cheers,

crowhill.

---

### Post by QIII on 2009-08-28
You may have installed Sun Java, but your machine may be using OpenJDK.

Some website developers either forget about the fact that some people use an open source alternative or deliberately snub it.  (OS-centric developers ...)

Could you post the results of 

```
 java -version 
```

---

### Post by crowhill on 2009-08-28
here it is

> $ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Client VM (build 14.0-b16, mixed mode, sharing)

---

### Post by QIII on 2009-08-28
Do you have any other Java apps that do not demonstrate this behavior?

---

### Post by crowhill on 2009-08-28
in firefox i go to [www.sagemath.org](www.sagemath.org) and java-drop-down-windows do not appear. however, this works ok in opera. if you know any other java aps that i could test let me know ...

---

### Post by QIII on 2009-08-28
I hope you won't be offended if I ask the following:

Do you have java enabled in FF (it probably is...) and do you have the plugin enabled?

---

### Post by crowhill on 2009-08-28
it appears i've got everything enabled ... see the attachment


the firefox problem could be a firefox/website problem only as it works with opera and other java stuff runs in firefox (like when i go to [http://www.freechess.org/Login/jin/applet.php](http://www.freechess.org/Login/jin/applet.php) the java thingee appears but if you hit enter as guest there's a blank/white window popping up ... the same with you?)

---

### Post by doas777 on 2009-08-28
when you installed the sun java, did you run a command like this one?
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by crowhill on 2009-08-28
either it was already included in the firefox version that came with ubuntu 9.04 or there was a drop-down window telling me that additional stuff is required for the website to show up correctly. i never used the command line for the java installation.

---

### Post by doas777 on 2009-08-28
> **crowhill said:**
> either it was already included in the firefox version that came with ubuntu 9.04 or there was a drop-down window telling me that additional stuff is required for the website to show up correctly. i never used the command line for the java installation.

if that is the case, then you likely have java installed, but the plugins are pointing to the open version (I believe it's called IcedTea).
try running that command (with firefox closed) and it may help.
also you can try installing the ubuntu-restricted-extras package, as that switches your alternatives as well.

---

### Post by crowhill on 2009-08-28
first, i run the command you posted above. after that, the firefox and, in particular, the maple (12 or 13) and jin (chess) problems are not resolved.

then, i installed the ubuntu-restriced-extras package and run that same command again. the problems remain.

when you go to [http://www.freechess.org/Login/jin/applet.php](http://www.freechess.org/Login/jin/applet.php) and try to login as guest (does not require an account) do you get the window showing up correctly? if so, which version of ubuntu are you using?

---

### Post by doas777 on 2009-08-28
this may be of use:
[http://www.tolaris.com/2009/04/08/sun-java-firefox-plugin-working-on-ubuntu-hardy-amd64/](http://www.tolaris.com/2009/04/08/sun-java-firefox-plugin-working-on-ubuntu-hardy-amd64/)

---

### Post by crowhill on 2009-08-28
thx for the link. i'm sorry, i should have indicated that i have a 32bit thingee.

anyways, i found a solution for the problem. however, it's not satisfactory. my metacity theme is such that there is no window title bar and there are no window borders either. if i go back to a theme with title and borders things work without problem. 

it'd be fantastic if there were another solution for the problem as i really like to have no borders and no title bar (a complete waste of space) for my windows.

---

### Post by doas777 on 2009-08-28
> **crowhill said:**
> thx for the link. i'm sorry, i should have indicated that i have a 32bit thingee.

anyways, i found a solution for the problem. however, it's not satisfactory. my metacity theme is such that there is no window title bar and there are no window borders either. if i go back to a theme with title and borders things work without problem. 

it'd be fantastic if there were another solution for the problem as i really like to have no borders and no title bar (a complete waste of space) for my windows.

weird. do you you have compiz enabled? if so have you tried disabling it?

---

### Post by crowhill on 2009-08-28
i don't have compiz installed. it's just a very simple metacity theme that i downloaded and modified a little bit.

now, my titlebar has the smallest hight possible and things work fine.

---

