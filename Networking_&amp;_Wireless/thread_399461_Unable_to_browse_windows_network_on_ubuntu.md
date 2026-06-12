---
title: "Unable to browse windows network on ubuntu"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by jaevel on 2007-04-02
Hi all,

Currently i can see all my file shares (files i shared on my ubuntu box) on my windows box but i cannot browse/see anything on my ubuntu box... i have installed smb4k and cups on ubuntu and managed to get it running to the point i can share files and printers. when i browse/scan the network i was able to see the "workgroup" but it keeps timing out while trying to connect?

i installed Ubuntu then installed the KDE desktop (not sure if this is even an issue) and this is a lan connection not wireless.. 

any help on this would greatly be appreciated...

Thanks in advance,
Jaevel

---

### Post by MontanaMax on 2007-04-02
I had a similar problem until I installed the samba client package - **smbclient **in the repository. Tthat enabled me to use the Kubuntu laptop to browse windows file shares.

---

### Post by jaevel on 2007-04-02
yeah, i have that installed too... i think i've installed everything i can think of related to this issue.. i know smbclient is installed... Still nothing.. i just dont understand why i can see shares from ubuntu box on windows just not the other way around?...

everything works, internet, file sharing, printer sharing all no prob. i just cant see or mount any network share... weird... 

Jaevel

---

### Post by jaevel on 2007-04-02
.

---

### Post by dolphin_oracle on 2007-04-02
Have you set up users on your ubuntu box for the laptop user.  For instance, when you log on to a share from your windows computer, the username and password must match BOTH your samba users list and your ubuntu users list.

---

### Post by jaevel on 2007-04-02
Maybe i don't understand.. let me try and explain the problem:

i have 2 computers on the network, computer 1=ubuntu and computer 2=win2k

1 shares 2 folders and 1 printer (MSGROUP)
2 shares 3 folders (WORKGROUP)

From the windows computer I can browse the network and see the folder being shared from ubuntu (MSGROUP) and can map printers/drives without problem. No passwords needed because i made all shares public in samba...

From ubuntu I open Smb4k and scan the network and see nothing (real quick like it didn't even really look), not even MSGROUP or WORKGROUP, using Konqueror and type smb:// i see "Workgroup" but i try and open it and i get "Timeout on server, Workgroup" and will not open... 

Why can I share files/printers from Ubuntu and see them from the windows box, but on ubuntu i cannot browse the network or see anything???

I dont know if this helps clear things up about my problem or not. i will try your suggestion, poke around and see about adding users to the samba accounts

Thanks for all the help so far everyone... i am looking forward to getting this resolved.. any further help would greatly be appreciated... 

Jaevel

---

### Post by dolphin_oracle on 2007-04-02
I don't know much about win2k, but do you have a setting like "File and Printer Sharing".  there may be two options, one for connecting to other shares, and one for letting your shares be browsed.  The later needs to be set on.

On my home mixed network, I have all the machnes (1 ubuntu, 1 xubuntu, and 2 winxp) all set to the same workgroup called MSHOME.  You may want to double check that all your machines are set to the same workgroup name.  I can browse shares from Nautilus.

---

### Post by DeusEx on 2007-04-05
you could try installing 'winbind'  and then running the 'smbtree'.
if that doesn't list your network it might be a firewall / wins server issue.
Do you have firestarter installed?

---

### Post by nkassi on 2007-04-05
Can you manually mount a file share by using the Connect To server wizard under Places ? 

I sounds like your windows computers are not allowing browsing or there share. Are you simply using a workgroup or are you on a domain ? 

Nic

---

