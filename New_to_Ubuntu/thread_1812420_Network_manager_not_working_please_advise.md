---
title: "Network manager not working please advise"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by Dhiren369 on 2011-07-26
Hello.
I just installed kubuntu 11.04 using wubi alongside windows 7. i set up a new DSL connection, but it never shows up and theres no option to connect. i read somewhere that this is a bug in kubuntu's network manager, and followed some instructions directing me to uninstall plasma network manager, and install nm-applet, which i understand is gnomes manager. now since i dont have internet on kubuntu, i downloaded nm-applet through 7, it was a named "network-manager-applet-0.8.3.998.tar"...but in kubuntu it says it cant recognise the file. I also lost my old KDE network manager since i uninstalled it, and i have errors reinstalling it... 

I am absolutely new to linux, and i really want to get in deep and learn more, but i cant seem to understand whats wrong. please dont post replies saying, 'if you cant figure it out, linux is not for you', cause everyones an amateur at some point right? I have no clue as to what to do. please help.

---

### Post by Peter09 on 2011-07-26
Are you able to establish a wired connection - you do not need network manager to do this. If so make sure your system is completely up to date.

---

### Post by androssofer on 2011-07-26
> please dont post replies saying, 'if you cant figure it out, linux is not for you', cause everyones an amateur at some point right? 

if you cant... na just kiddin. wudnt worry about tht, aint many flamers on these forums, people here r almost always helpful and friendly :-).

not sure how to get from where you are to get it working again...

what i would do is uninstall ur wubi, then reinstall. then download the gnome network manager first, then uninstall KDEs 1... 

but sum1 else will prob know how to fix it as is, so tht can b ur back up plan ;-)

---

### Post by Dhiren369 on 2011-07-26
wow, i cant believe i got replies in two minutes:)...the problem will repeat if i uninstall wubi, i did install it twice..and i cant get anywhere because i cant connect through the internet through kubuntu, so the only way i can solve this problems internet needs is through windows 7, by downloading a new netwrrking manager or something i suppose...even when i add a new dsl connection, theres no option to actually connect, it says no connections...it detects ethernet as eth0 thought..im pretty sure the network managers zoinked i read it  in a few places but none of those places offered usable solutions, hence me signing up to ubuntuforums:) i hope this problem gets solverd damn

---

### Post by Peter09 on 2011-07-26
Mmmm - always found wubi a problem - I can only advise to dual boot, its a much better option in the long run.If you decide to do this its always safer to do a backup first. Other than that the installer will walk you through setting up dual boot no problems.

---

### Post by Dhiren369 on 2011-07-26
where can i install a wired connection then? u mean through the terminal Kconsole??

---

### Post by Peter09 on 2011-07-26
Wired connection should already be enabled - just get a wire to your router from your machine.

---

### Post by Dhiren369 on 2011-07-26
i love kubuntu's kde interface, when i install ubuntu's gnome through wubi network works just fine....i really want to continue using kubuntu, but this networking problem is a big big hurdle ..does anyone know of a workaround?

---

### Post by Dhiren369 on 2011-07-26
it detects a wired connection, but theres no place i can use my login details to connect to the internet

---

### Post by androssofer on 2011-07-26
> **Dhiren369 said:**
> wow, i cant believe i got replies in two minutes:)...the problem will repeat if i uninstall wubi, i did install it twice..and i cant get anywhere because i cant connect through the internet through kubuntu, so the only way i can solve this problems internet needs is through windows 7, by downloading a new netwrrking manager or something i suppose...even when i add a new dsl connection, theres no option to actually connect, it says no connections...it detects ethernet as eth0 thought..im pretty sure the network managers zoinked i read it  in a few places but none of those places offered usable solutions, hence me signing up to ubuntuforums:) i hope this problem gets solverd damn

from i gather u have 2 options:

go [here]("http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/") and find the .deb file for network manager you want, download in windows. fire up ubuntu and open it.

or download the main ubuntu, burn it to disk. disable web repositories: [this tells you how]("https://help.ubuntu.com/community/Repositories/Kubuntu"), then put in the ubuntu cd and do:

```
sudo apt-cdrom add
sudo apt-get install network-manager-gnome
```

in your terminal. do 1 line, hit enter, paste in the next then hit enter. and tht should work... key word being should...

---

### Post by Peter09 on 2011-07-26
You should not need login details, once you are on a wired connection it should already be setup. Try using a browser.

---

### Post by androssofer on 2011-07-26
> **Peter09 said:**
> You should not need login details, once you are on a wired connection it should already be setup. Try using a browser.

Dhiren369 said:

> i set up a new DSL connection he might not have a router to be able to plug in the ethernet? or get a connection through...

---

### Post by Dhiren369 on 2011-07-26
thanks! although could you help me out decide what file to download for kubuntu? i dont understand extensions, does .deb work in kde or its only gnome? i think it does...please could you select a network manager LIKE the one in ubunto BUT not the default one in KUBUNTU?

---

### Post by Peter09 on 2011-07-26
Ahhh - 
 
>  
he might not have a router to be able to plug in the ethernet? or get a connection through...

 
you are right .... (I think)

---

### Post by androssofer on 2011-07-26
> **Dhiren369 said:**
> thanks! although could you help me out decide what file to download for kubuntu? i dont understand extensions, does .deb work in kde or its only gnome? i think it does...please could you select a network manager LIKE the one in ubunto BUT not the default one in KUBUNTU?

.deb files work in kubuntu according to [this]("http://linux.about.com/od/kubuntu_doc/a/kubudg21t02.htm")

but you might b best with the cd plan, as it will have the right 1. then if u get it working in some way, u can run update manager and have the latest and greatest. I hav no idea which file to download...

---

### Post by Peter09 on 2011-07-26
try running
 
 ```
knetworkmanager
```
 
(not underlined) in a terminal

---

### Post by Dhiren369 on 2011-07-26
ill try knetwork manager...switching between kubuntu and 7 for internet is driving me nuts :p i tried installing this .deb , it gave me an error...i have a screenshot

---

### Post by Dhiren369 on 2011-07-26
by fire up ubuntu you do mean Kubuntu right?

---

### Post by Peter09 on 2011-07-26
in kubuntu - in a terminal - run ```
knetworkmanager
```

---

### Post by androssofer on 2011-07-26
> **Dhiren369 said:**
> ill try knetwork manager...switching between kubuntu and 7 for internet is driving me nuts :p i tried installing this .deb , it gave me an error...i have a screenshot

dependencies... grr. def go with the cd idea. 

load kubuntu, disable web repositories, then install from cd... tht shud handle the dependencies for you.

---

### Post by Dhiren369 on 2011-07-26
damn i did some ****..with the knetwork manager...and it somehow got working..the internet! woohoo..problem is i do not know what i actually did, and i think i may not be able to connect the next time..lets hope it doesnt happen!! heres a screenshot again..it only shows enable networking!

---

