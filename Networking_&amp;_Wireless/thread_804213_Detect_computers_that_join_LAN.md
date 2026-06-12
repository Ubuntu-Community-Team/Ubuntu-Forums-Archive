---
title: "Detect computers that join LAN"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by azredwing on 2008-05-22
Hi all,

I have a notebook and a desktop that are both running Hardy. The /home directory is essentially exactly the same, and I'm using rsync to keep the two in sync. 

Right now I've got a bash script that syncs the directories I need to be synced in place, but I'd like to have a way to dynamically do so whenever both computers enter the network for the first time (if one computer was previously on and the next computer was just turned on.)

Is there a way (in any language, but I know C and Perl best, and I'm okay with bash) to be able to detect when a computer has joined the network? I'd like to be able to something like this (pseudo-code):

```

while (1){
    if ($notebook_joined_network){
        begin_rsync_procedure();
    }
    else{
       sleep();
    }
}

```


Any ideas on how to do this?

---

### Post by tamoneya on 2008-05-22
i would assign it a static IP on your local network and then just attempt to ping that IP.  If you get a response do a rsync.  If it doesnt try again later.

---

