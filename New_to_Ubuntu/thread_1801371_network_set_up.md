---
title: "network set up"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by Walkerst on 2011-07-10
I have just installed Ubuntu 5.0 and want to learn how to set up a local network which will include my wife's windows vista (yuk) machine.  Can't seem to find the network settings to be able to set it up and need some guidance as to what to put in as well.

---

### Post by spiky001 on 2011-07-10
Why are you using ubuntu 5 ??? 11.04 is latest, 10.04 is latest long term support

---

### Post by Rex Bouwense on 2011-07-10
Recommend that you use a newer (and still supported version) of Ubuntu as Spikey001 suggested.  You also need to provide us with a little more information for anyone to provide you with some assistance.  For a starter will this be a wired or wireless LAN?

---

### Post by Walkerst on 2011-07-10
Sorry all, was looking at the wrong software when quoting the version of Ubuntu, am using 11.04:(

This is for a wireless network which will have a QNAP NAS box attached to it when it arrives.

---

### Post by Jacobonbuntu on 2011-07-10
> **Walkerst said:**
> Sorry all, was looking at the wrong software when quoting the version of Ubuntu, am using 11.04:(

This is for a wireless network which will have a QNAP NAS box attached to it when it arrives.

that's a good one :P!
to *connect* to the network is one thing. I assume you will connect the NAS (wired) to the wireless router, to share it with all computers in the network. apart from that, will you need to share files/directories* between the computers*?

---

### Post by Walkerst on 2011-07-10
Yes the NAS will be a direct connection (wired). And Yes to file and Directory sharing.

Have had a look in the 'start up applications preferences' but it says that 

"this feature could not be enabled because the required packages are not installed on your system" but does not state what the packages are.

---

### Post by Jacobonbuntu on 2011-07-10
forgive me for asking, you will probably know this already, but is there no network-indicator icon in the right/upper corner of your screen? every "normal" installation of Ubuntu has most of the network software installed by default.

---

### Post by Walkerst on 2011-07-10
I have a wireless router that I have the wireless connection icon in the top right hand side of the workspace

---

### Post by Morbius1 on 2011-07-10
> **Walkerst said:**
> Have had a look in the 'start up applications preferences' but it says that 

"this feature could not be enabled because the required packages are not installed on your system" but does not state what the packages are.
I'll be honest, I don't know if this is a networking question or a file sharing question but...

There is only one application that will show you that exact error and it's not in Start up application. It's called [COLOR=Blue]**Personal File Sharing**[/COLOR].

If you have a Windows machine in your network you don't want to use Personal File Sharing . You want to use Samba.

What is the output of the following command:
```
smbtree
```

---

### Post by Jacobonbuntu on 2011-07-10
> **Morbius1 said:**
> I'll be honest, I don't know if this is a networking question or a file sharing question but...

There is only one application that will show you that exact error and it's not in Start up application. It's called [COLOR=Blue]**Personal File Sharing**[/COLOR].

If you have a Windows machine in your network you don't want to use Personal File Sharing . You want to use Samba.

What is the output of the following command:
```
smbtree
```

......indeed the question is not clear, and to broad to answer. Without specifically explaining what is it that you wish to set up, and what  the problems are that you encounter, there is a lot to say about networking \\:D/.

---

### Post by Walkerst on 2011-07-10
it is \\WALKER-AMILO

---

### Post by Morbius1 on 2011-07-10
That can't be right but for the sake of discussion is WALKER-AMILO      the Linux box or the Vista box?

If it's the Linux box is the Vista box up and running and connected to the network?

[COLOR=Blue]**EDIT**[/COLOR]: If the Vista machine is up and connected to the network please post the output of this command:
```
ip neighbor show
```

---

