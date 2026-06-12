---
title: "network scanning tool"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by aliyanage on 2006-12-13
Hi all,

Maybe you can help me out with this or give me a hint...
I am looking for a tool to scan the whole network that I am in right now, is there a good tool for this or is there a way to do this over the shell.

when using windows I used ip scan angry, maybe your familiar with it. basically I am looking for something simialar. Would be really thankful for some suggestions...

aliyanage

---

### Post by gerowen on 2006-12-13
Yeah I've used Angry IP Scanner.  You may be able to continue using it with wine.

---

### Post by ciscosurfer on 2006-12-13
Would **System > Administration > Network Tools** work for you?

---

### Post by aliyanage on 2006-12-13
nope won't work for me, well depending on what I want but the thing is that I just want a list of all ip's if possible with hostnames when scanning, and the network tools coming with ubuntu can't do that...

Wine would be an option but I want to try get away 100% from windows and start working only with ubuntu based apps and tools...

---

### Post by ciscosurfer on 2006-12-13
Perhaps this page will help: [http://doc.gwos.org/index.php/SecurityAnalysis](http://doc.gwos.org/index.php/SecurityAnalysis)

---

### Post by aliyanage on 2006-12-13
thanks a lot for helping out with that link. I used nmap which worked fine, really cool thing, it gives you the hostname, ip address, up or down status and you can scan for a lot more things...

thanks again

---

### Post by FrodoB on 2006-12-13
You need nmap: ( You may need to open up repositories in /etc/apt/sources.list, if it can't be found)

sudo apt-get install nmap

sudo apt-get install nmapfe

then look in:

Applications -> Internet -> NmapFE

or at a terminal prompt:

nmap

See the OS detection feature.

Also see:

[http://insecure.org/nmap/](http://insecure.org/nmap/)

---

### Post by aliyanage on 2006-12-13
thanks for that info, will try first with the bash, I love to work with bash but in case I don't get any resolution or don't know how to work this out I'll switch to the graphical... :-D

---

### Post by FrodoB on 2006-12-13
I prefer to use bash as well. The nice thing about having the GUI is that it shows you the command line at the bottom of the page for your use later. Sometimes this is quicker than reading the manual.

---

### Post by tturrisi on 2006-12-13
just type:
~# nmap
or
~# nmap -h
to get what switches you can use.
Note the difference between O and 0 (cap o & zero)

# nmap -v -sP 192.168.0.0/100
will give you all local comps up to 192.168.0.100

---

### Post by aliyanage on 2006-12-13
oh cool, exactly the command I was looking for instead of typing in the range :-D

---

