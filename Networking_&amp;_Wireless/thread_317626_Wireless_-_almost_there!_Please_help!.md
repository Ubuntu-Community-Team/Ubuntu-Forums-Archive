---
title: "Wireless - almost there! Please help!"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by maggot_brain on 2006-12-12
Hello everyone,

I've managed to get my wireless card (Buffalo WLI-U2-KG54, rt2570 based)connected to the network when it is unencrypted but I am having problems accessing it via WPA AES encryption.

The problem is when I use the iwpriv command to say for example:
```

iwpriv rausb0 set AuthMode=WPAPSK
```

I get a message saying:

```
invalid command: set
```

My wireless cards is a ralink based USB device and as I've said it is working fine if the signal is unencrypted.  The Ubuntu wiki states that I should use iwpriv and not wpa_supplicant.  Here is the output of iwpriv if it helps:```


rausb0    Available private ioctls :
          auth             (8BE0) : set   1 int   & get   0      
          enc              (8BE1) : set   1 int   & get   0      
          wpapsk           (8BE2) : set  64 char  & get   0      
          psm              (8BE3) : set   1 int   & get   0      
          adhocmode        (8BE4) : set   1 int   & get   0      
          rfmontx          (8BE5) : set   1 int   & get   1 char 
          forceprismheader (8BE6) : set   1 int   & get   0    
```  

I'm using the guide from here:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

The docs on the drivers from [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) that I am using state that I should use iwpriv.

Any help would be greatly appreciated!

Ananda

---

### Post by FrodoB on 2006-12-12
I suppose you have looked at this? It is not exactly your chipset, but it is Ralink.

[http://www.ubuntuforums.org/showthread.php?t=78250&highlight=rt2500](http://www.ubuntuforums.org/showthread.php?t=78250&highlight=rt2500)

---

### Post by maggot_brain on 2006-12-12
I'm sorry but I don't understand your reply.  What I really need is help with the iwpriv command.

thanks,

Ananda

---

### Post by FrodoB on 2006-12-12
Sorry forgot to paste the link.  It is discussed in the link that is now in the previous post.

---

### Post by maggot_brain on 2006-12-12
Thanks for the reply.  I tried the method mentioned in the post about the rt2500 card.  This is when I get the iwpriv 'invalid set command'  error.

Ananda

---

### Post by FrodoB on 2006-12-12
A bit beyond me then. I suppose you did start every command with sudo?

sudo iwpriv ..................

---

### Post by maggot_brain on 2006-12-13
No I re-enabled the root account so I can log in as root on the console...

---

### Post by Gast00n on 2007-03-31
I got the same kind of problem with airtun-ng, using aircrack0.7 & ubuntu 7.04 BETA, and the same solution worked :)

---

