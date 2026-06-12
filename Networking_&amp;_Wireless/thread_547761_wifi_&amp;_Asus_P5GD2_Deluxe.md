---
title: "wifi &amp; Asus P5GD2 Deluxe"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by indicerappeur on 2007-09-10
Hello everyone,

Lately I've installed Ubuntu Feisty on my desktop. My mobo is an Asus P5GD2 Deluxe which is shipped with wifi.

My wifi connection works perfectly on Windows but I can't achieve to make it work with Ubuntu. I managed several times to install the driver through ndiswrapper but it doesn't work.

Indeed, after I install the wifi driver, I can see my wifi hardware and set up network options. But when I launch Firefox the web page starts loading and everything seems to work during 3 or 4 seconds and then my system freezes suddenly. Everytime I need to hard boot my computer.

I read many things on ndiswrapper and wifi on the web but I can't get rid of that problem. Please does anyone have a few tips to make my Ubuntu fully functionnal?

Thank you in advance.

---

### Post by indicerappeur on 2007-09-11
Please anybody help.

---

### Post by rootshooter on 2007-09-13
Hi, I have this motherboard and wifi works for me. I use ndiswrapper with win2k driver.
When I installed ndiswrapper for first time, I used winXP driver and the kernel freezed when I set essid. Then I used win2k driver and It was Ok. 
Try this

---

### Post by indicerappeur on 2007-09-16
Thank you for your answer

I installed :
- ndiswrapper common 1.38 (not the latest version but I don't know how to compile and want to avoid it for the moment)
- ndiswrapper utils 1.9.

I downloaded the wifi drivers for my Asus P5GD2 Deluxe. There are 3 files :
- mrv8ka50.sys
- mrv8ka51.inf
- mrv8knet.cat

Following the instructions given on Ubuntu website I input the following command :
```
emmanuel@emmanuel-desktop:/home$ sudo ndiswrapper-1.9 -i mrv8ka51.inf
```

But it says :
> installing mrv8ka51 ...
couldn't open mrv8ka51.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.

And when I try ```
ndiswrapper -l
``` it warns me the driver is invalid.

---

### Post by tucano on 2007-09-18
hi!

I saw this post and tried to install ndiswrapper with apt-get, then I installed ONLY the *.inf  driver for XP, and seemed to go everything ok, infact

```
ndiswrapper -l
```

says ok, I also configured it following this document from point 2:

```
1. Disabilitiamo i driver open
Da terminale digitiamo:
sudo gedit /etc/modprobe.d/blacklist

ed aggiungiamo in coda al file le righe:
#Disabilito i driver della scheda Wireless del Kernel
blacklist bcm43xx

A questo punto riavviamo il computer.

2. Installiamo ndiswrapper
Installiamo ndiswrapper con il comando:
sudo apt-get install ndiswrapper-utils-1.9

se stiamo usando Ubuntu 7.04 Feisty Fawn, se invece abbiamo una versione precedente digitiamo:
sudo apt-get install ndiswrapper-utils

2. Installiamo i driver
Ora ci servono i driver per Windows della nostra scheda. Precisamente abbiamo bisogno dei files bcmwl5.inf e bcmwl5.sys. Possiamo trovarli nel cd dei driver per Windows oppure potete scaricare i miei che ho preparato in un archivio e che funzionano alla perfezione con le Broadcom 4318.

Dopo aver recuperato i files necessari da terminale spostatevi nella cartella in cui questi sono situati e digitate:
sudo ndiswrapper -i bcmwl5.inf

Dopodiché verificate che i driver siano stati installati correttamente digitando:
ndiswrapper -l

Adesso digitate da terminale:
sudo ndiswrapper -m
sudo gedit /etc/modprobe.d/ndiswrapper

Nel file che si aprirà aggiungete la riga:
alias eth1 ndiswrapper

Ora aggiungiamo i driver di ndiswrapper ai moduli da caricare all’avvio:
sudo gedit /etc/modules

e aggiungete alla fine del file la riga:
ndiswrapper

Ora potete tranquillamente riavviare il pc e godervi la vostra scheda wireless ;) 
```

Now I can connect with wireless, it scans for networks, connect to networks, ping outside my network, but it doesn't open web pages...

I already turned ipv6 off (in kernel and in firefox) following this:

```
Disabilitare il supporto a ipv6 è facile non comporta alcun rischio.

Aprire il file /etc/modprobe.d/aliases

sudo gedit /etc/modprobe.d/aliases

Cercare la riga
alias net-pf-10 ipv6

e sostituitela con
alias net-pf-10 off #ipv6

Inserire sotto quest’ultima, anche la riga seguente:
alias ipv6 off

Salvate il file e chiudete.

Adesso mettiamo in blacklist il modulo ipv6:

sudo gedit /etc/modprobe.d/blacklist

inserire in fondo al file di testo la seguente riga:
blacklist ipv6

Salvate e chiudete pure questo file.

Ultimo passo: disabilitare ipv6 in Firefox.

Aprire Firefox e digitare about:config nella barra degli indirizzi.
Cercate la chiave network.dns.disableIPv6 e cambiatene il valore da FALSE a TRUE.
```


What can I do now??

---

### Post by indicerappeur on 2007-09-18
Hey what are you doing???? [-X

Post your message somewhere else tucano it has nothing to do here. I've been trying to set my connection for weeks and when I ask for some help I don't want to see people taking advantage of my thread to solve their own problem.

---

### Post by tucano on 2007-09-18
I posted here because we have the same problem, the same motherboard and the same operating system. Anyway I posted in a separate thread.

[COLOR="Red"]I think forums are for helping people, and yours is the behaviour of a person who wants to be helped from others, but doesn't want to help them.[/COLOR]

---

### Post by indicerappeur on 2007-09-18
Forums are not places for mess and anarchy. I've got one specific problem so I made one thread to get some specific help. I don't have any lessons of morals to learn from you. I helped people many times through forums about windows problems, and unlike you, I respect other forumers.

> **tucano said:**
> [COLOR="Red"]I think forums are for helping people, and yours is the behaviour of a person who wants to be helped from others, but doesn't want to help them.[/COLOR]

---

### Post by tucano on 2007-09-18
1) The guides I posted could be useful to you too

2) I have the same problem so I have th right to follow the topic and I have the right to post

3) you are offensive in my comparisons saying you have nothing to learn from me. stop it

Now stop with the O.T. this is a linux forum, not your chat

---

### Post by indicerappeur on 2007-09-19
"you are offensive in my comparisons saying you have nothing to learn from me. stop it"

--> Be serious, you tried to give me lessons of morals by stating that I don't help anyone. You don't know anything about me and you judge me. And now you'd like to prevent me from answering you. Come on guy you're not serious.  Be clear, organized, respectful to other people, let them answer, don't behave as a general and you will be considered as an adult.

---

### Post by indicerappeur on 2007-09-19
I installed :
- ndiswrapper common 1.38 (not the latest version but I don't know how to compile and want to avoid it for the moment)
- ndiswrapper utils 1.9.

I downloaded the wifi drivers for my Asus P5GD2 Deluxe. There are 3 files :
- mrv8ka50.sys
- mrv8ka51.inf
- mrv8knet.cat

Following the instructions given on Ubuntu website I input the following command :
Code:

emmanuel@emmanuel-desktop:/home$ sudo ndiswrapper-1.9 -i mrv8ka51.inf

But it says :
Quote:
installing mrv8ka51 ...
couldn't open mrv8ka51.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.
And when I try
Code:

ndiswrapper -l

it warns me the driver is invalid.

---

### Post by PhatBoy on 2007-09-26
Just a thought - I seem to remember that ndiswrapper requires that the .sys and .inf files have the same names... might be remembering wrong though as I haven't used it in a while.

I did have it working on a P5GD2 under Edgy, I believe with the Win2k drivers and I definitely remember having to rename one of the files as the zip I downloaded had the name in caps, I think it was the .sys file.

---

### Post by indicerappeur on 2007-09-28
OK thank you very much for your advice phatboy I will try it tonight and report back.

---

### Post by Count Doofus on 2007-10-21
I had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was  every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
 I got -  No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE    -  Mrv8000c.INF -  

GRRRRRRRRR!%@$#$###!$!@@!$@!@#! 

hey author great code I really works like a charm ! 
OHHH AND  Thanx a bunch for making it case ensitive and letting us in on the secret   !!!!!!&%^@#&^@%#$&#^%@&#$%

---

### Post by Count Doofus on 2007-10-21
Yeah I just Double Checked the CASE for your driver

MRV8KNT.INF

Here is how it was listed in the .INF File

;===========================================================================
; Source Media Information Sections
;===========================================================================
[SourceDisksNames]
1 = "Marvell installation disk 1",,,

[SourceDisksFiles]
; On Marvell installation disk 1 
MRV8K50.sys =1
mrv8k51.sys =1
mrv8kx64.sys =1

Nothing Like a good cryptic error when you think you've structured your command RIGHT. Windows spoiled me and made me loose my attention to detail.

---

### Post by Count Doofus on 2007-10-21
Count DoofusOctober 21st, 2007, 11:51 AM
I had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

In the CASE for your driver with MRV8KNT.INF
 Bla@blabla:~$ sudo ndiswrapper -i MRV8KNT.INF

OHHH by the way MRV8KNT = Mr Vacant nice touch !!!!

Here is how it was listed in the .INF File

;================================================= ==========================
; Source Media Information Sections
;================================================= ==========================
[SourceDisksNames]
1 = "Marvell installation disk 1",,,

[SourceDisksFiles]
; On Marvell installation disk 1 
MRV8K50.sys =1
mrv8k51.sys =1
mrv8kx64.sys =1

GRRRRRRRRR!%@$#$###!$!@@!$@!@#! 

Remember

---

