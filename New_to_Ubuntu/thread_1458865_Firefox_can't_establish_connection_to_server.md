---
title: "Firefox can't establish connection to server"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by ITIZI on 2010-04-20
Hey everybody, i'm still new to ubuntu but i'm a capable person and have made the switch from windows, yay! So my problem i believe is within firefox or ubuntu because i can connect to the same server when i boot up using windows7. Anyway, i don't know much about networks and such and i was hoping someone could help me out with this. Here is a copy of the error message i get:

Unable to connect

Firefox can't establish a connection to the server at ftp.idsoftware.com.      
      
    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

I know this has to do with gaming but i get the same message when i try to connect to my schools email server. What i have tried on my own is disabling my firewall, temporarily, and it had no effect so i know its not my firewall however i haven't a clue about proxy's or how they work so maybe it's that? I also know its not either of the other two problems because i wouldn't be posting this if i had that severe of a network problem. Any help at all with this would be greatly appreciated thank you!

---

### Post by Silvertones on 2010-04-20
Are you on a network? Are you connecting to this site OK?

---

### Post by scottiw2000 on 2010-04-20
It looks to me like you're trying to connect to an ftp server rather than a regular web page. Usually Firefox doesn't handle ftp very well. If I have to upload or download files using ftp I usually use the FireFTP plugin for Firefox or just type the address of the ftp server into the location bar of Nautilus (the standard Ubuntu file manager). What does this page usually do when you access it in Windows? When you use it in Windows do you access it using Firefox or using Internet Explorer? My impression is that IE has a bit more flexibility for doing ftp transfers in the main browser window, but I suspect this comes with some security trade-offs.

---

### Post by wojox on 2010-04-20
Can you connect through it's ip address: [http://192.246.40.185/](http://192.246.40.185/)

---

### Post by ITIZI on 2010-04-21
Ok, i'm able to connect to other websites and surf the net just fine, I can even connect through the ip address given.

I am connecting to an ftp server heres the address:[ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run](ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run)

I got the "Fireftp" add-on installed I'm reading through the support pages to figure out how to work it.

I've tried the nautilus thing though I'm not sure if you meant use the "Connect To Server..." button or app because that doesn't work either I keep getting an error message: Cannot display location "ftp://anonymous@ftp:0//ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run%0A:21" Error resolving 'ftp': No address associated with hostname

I'm not sure what all that means other than i cant connect to the server still, lol. Any other suggestions would be helpful I'll give any idea a shot and I appreciate the help from everyone so far, thanks.

---

### Post by ITIZI on 2010-04-21
Well, I'm stumped now... I've been trying to connect to the server using FireFTP and I keep getting "Unable to make connection. Please try again later." error. I've tried changing the connection type to almost every combination possible hoping to get lucky and nothing has worked. If anyone is able to help me further that would be great, I could use the help. Oh and I tested making a connection to my schools email server and I just kept getting the same message so IDK. I would really like to figure this out because I could do away with windows all together and quit using it as a crutch for when things get beyond my abilities with Ubuntu.

---

### Post by wojox on 2010-04-21
Open a new tab and put this as the url:

```
ftp://ftp.idsoftware.com/
```

What is it your trying to do?

---

### Post by ITIZI on 2010-04-24
I'm trying to download the updates for quake 3 but I'm unable to connect to the ftp server.  I keep getting the same error message "Firefox is unable to establish a connection to .... server." I've tried several ftp apps from synaptic package manager and the FireFTP add-on for Firefox and nothing will connect.  I'm using Ubuntu 9.10 on my laptop i'm wondering if i should try installing the netbook version to see if it makes a difference even though i haven't had any issues otherwise with straight up 9.10.  Oh and it's not just id software's server it's any ftp server, i've tried connecting to several different servers to see if it was only id software i couldn't connect to. HELP IDK WTF is wrong and i'm ready to start going to extremes to solve the issue.

---

### Post by RedRat on 2010-04-24
> **wojox said:**
> Open a new tab and put this as the url:

```
ftp://ftp.idsoftware.com/
```What is it your trying to do?
I tried this in FireFox and I am running 8.04 Hardy, and I could connect and see all the directories. Hmm. Is someone in your household blocking gaming sites like that? Maybe your ISP? 

worked fine for me.

---

### Post by ITIZI on 2010-04-24
I don't know for certain.  I'm pretty sure it's my computer because I haven't been able to connect to my schools email sever even when I'm logged into their wi-fi access.  The other reason for thinking this is I can access the server when I boot up with windows.  I think that I might try using an earlier version of Ubuntu to see if that will resolve the issue.  Time to start backing stuff up. :(

---

### Post by RedRat on 2010-04-24
> **ITIZI said:**
> I don't know for certain.  I'm pretty sure it's my computer because I haven't been able to connect to my schools email sever even when I'm logged into their wi-fi access.  The other reason for thinking this is I can access the server when I boot up with windows.  I think that I might try using an earlier version of Ubuntu to see if that will resolve the issue.  Time to start backing stuff up. :(

Are you running a firewall in Ubuntu? How about using something like Opera or Chrome? I am wondering if you don't have a site that is 'blacklisted' in FireFox. Does sound strange.

---

### Post by shutterbc on 2010-04-24
Edit: nevermind, I just realized you were able to get to some sites.

---

### Post by ITIZI on 2010-04-25
> **RedRat said:**
> Are you running a firewall in Ubuntu? How about using something like Opera or Chrome? I am wondering if you don't have a site that is 'blacklisted' in FireFox. Does sound strange.

Yeah I'm using firestarter, when I first had issues it was with my schools email server and Firefox suggested I disable my firewall.  So I tried that and it didn't make a difference, so IDK whats up.  In any case I've gotten all my stuff backed up now and I'm gonna try installing Ubuntu 9.04 tonight and see if it makes a difference.

---

### Post by ITIZI on 2010-04-29
Well, I appreciate all the input I got on how to go about fixing this issue.  I presume it had something to do with the dual boot I had going.  From what I've read I'm not the only one that's had issues like this.  So my solution ended up being a fresh install and wiping out the dual boot.  Thanks everybody.

---

