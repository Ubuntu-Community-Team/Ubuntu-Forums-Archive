---
title: "very slow downloads using upate manager"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by rpennington on 2009-02-12
I have just installed ubuntu 8.04.02 on a Dell e6400 laptop.
When I try to download files via any of the gui apps, such as firefox, update manager, or synaptic package manager, I get very slow throughput.
The performance can drop below 1K bytes/sec.  Using ftp from the commandline to access one of the same sites I can get over 700K Bytes/Sec sustained on large files.

Any clues as to what is causing the slow performance for the normal applications for get updates and such?

---

### Post by donkyhotay on 2009-02-12
> **rpennington said:**
> I have just installed ubuntu 8.04.02 on a Dell e6400 laptop.
When I try to download files via any of the gui apps, such as firefox, update manager, or synaptic package manager, I get very slow throughput.
The performance can drop below 1K bytes/sec.  Using ftp from the commandline to access one of the same sites I can get over 700K Bytes/Sec sustained on large files.

Any clues as to what is causing the slow performance for the normal applications for get updates and such?

I don't know how to fix the problem but I can tell you thats not normal. The only time I've ever seen exceptionally slow downloads with synaptic is when a new version is bing released but thats to be expected when almost everybody is upgrading at the same time.

---

### Post by mick316 on 2009-02-12
Synaptic has a feature called select best server.. it tests  by pinging all the servers and gives you the fastest repo.

---

### Post by jemate18 on 2009-02-12
Yes try the synaptic select best server... Or you can choose the server closest to you......

---

### Post by donkyhotay on 2009-02-12
> **mick316 said:**
> Synaptic has a feature called select best server.. it tests  by pinging all the servers and gives you the fastest repo.

Forgot about that, thats a good idea. If you don't know how to do that rpennington then go into "system > admininstration > software sources". You'll see an option to 'download from' and choose 'other' from the dropdown list. You'll see a button to 'select best server' which will cause the program to find the best server for you based off ping times. You'll then need to reload the repositories.

---

### Post by rpennington on 2009-02-12
What about the following case. 

 I use firefox to go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) site.  I select a version of iso to download and select an ftp site.  In most cases I have been selecting lug.mtu.edu for the download site, and I get very poor results. 
 If I do an anonymous ftp from the command line to the same site, I get over 700KBytes/Sec.  

I have also tried the Walla Walla University site with firefox and still got the < 10KBytes/sec.

---

### Post by rpennington on 2009-02-12
Additional information,

I tried retrieving the file using wget from the command line,

wget [http://lug.mtu.edu/ubuntu-releases/intrepid/ubuntu-8.10-desktop-i386.iso](http://lug.mtu.edu/ubuntu-releases/intrepid/ubuntu-8.10-desktop-i386.iso)

and I get the same poor performance.  The first minute is great and then it drops down to less than 10K/sec.

---

### Post by donkyhotay on 2009-02-12
Do you have FTP selected as the protocol when you choose the server to download from? Maybe HTTP (default) is being throttled for those servers.

---

### Post by rpennington on 2009-02-12
I tried the wget set to use ftp and it too slowed down to less than 10K/sec.

But if I ftp to the same site from the command line, then cd to the appropiate directory and issue a get for the file, I get 700K/sec.

---

### Post by Maheriano on 2009-02-12
I had this issue when using a wireless card in my desktop with the wrong drivers. Once I plugged in wired it worked perfect and then once I got the correct driver via the updates, the wireless card worked perfect.

---

