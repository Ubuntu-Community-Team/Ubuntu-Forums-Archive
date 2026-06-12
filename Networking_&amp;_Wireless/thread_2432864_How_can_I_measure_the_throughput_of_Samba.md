---
title: "How can I measure the throughput of Samba?"
date: 2019-12-10
forum: Networking &amp; Wireless
---

### Post by Hans_van_Leeuwen on 2019-12-10
How can I measure the throughput of Samba?
I want to know how much bytes of data enters or leaves the samba server via Samba.
Do you know a command to get that numbers?

---

### Post by lensman3 on 2019-12-11
I don't know of a command that will tell you the throughput but you can try this:

FIll up the junk file on the exported samba drive. Copy the "junk" file to a different machine using the samba exported drive.  Time the results!  Divide bytes by seconds.  This is rather low-tech.

"cat /dev/urandom >junk" 

"cp junk otherfile"

---

### Post by guiverc on 2019-12-11
I likewise don't know of any specific command to view only a SaMBa's throughput.  I'd to likely just time something

eg.
```
time cat /de2900/nix_iso/lubuntu-18.10-desktop-i386.iso >/dev/null
```

which has the system record time, and if it's a known size of file you're reading...

Other alternatives that come to mind are maybe watching `iotop`, but monitoring tools are only rough clues I suspect...

---

### Post by webaake on 2019-12-12
Take a look at bwm-mg. Measures throughput in various ways.

---

### Post by Hans_van_Leeuwen on 2019-12-13
Copying a (big) file to a Samba-drive is not what I need.
This measure the speed of Samba and not the throughput.
I need to know how intensive Samba is used.
A "time cat" is only useful if it concerns a big file and a big file loads the network.

I could not find anything about "bwm-mg" except then that it is a car.

---

### Post by SeijiSensei on 2019-12-13
Samba isn't any more or less "intensive" than any other TCP service. I'm not sure what you're expecting to find. In particular, I don't know what you mean by "throughput." Samba transfers files between a server and its clients. Nothing is going "though" the server.

---

### Post by webaake on 2019-12-13
Well Google isn't always your friend. Try something else, like  apt search bwm-ng......

---

### Post by lensman3 on 2019-12-14
Take a look at the "time" program.  You can pop time into the background running samba.  

"time samba"

---

### Post by hk42 on 2019-12-15
Samba is used to share data with non Linux devices the best is to use them to
compare performances.
On the Linux side Midnight commander indicates the speed when copying files.
My experience is that the file system used to store the data is important too.

---

### Post by Hans_van_Leeuwen on 2019-12-17
Apparently I failed to explain what is my wish.
Customers upload big files to our Linux SFTP-server.
Colleagues download that big files from that Linux SFTP-server to their Windows systems by Samba.
I  measure the network load of that SFTP-server with SNMP.
If the network load exceeds a limit I get a message.
At such a moment I want to know if most of the network load goes via SFTP or via Samba.


I found bwm-ng (and not bwm-mg). 
But bwm-ng shows the total Rx and Tx load of the network interface.
And not separately for the SFTP of SaMBa protocol.

 How can I measure the network load caused by up or down loads by Samba?

---

