---
title: "medibuntu mystery"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by nnjond on 2009-03-14
hi, Ive tried to install medibuntu but it has not gone smoothly. Ive been hit by so much jargon i don,t know what to do! It begins with my command:

nnjond@nnjond-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
[sudo] password for nnjond: 
--2009-03-14 10:54:56--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 230         --.-K/s   in 0s      

2009-03-14 10:54:56 (25.7 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]

nnjond@nnjond-laptop:~$ 


But when i open add and remove i get...


W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783



What,s going on?

---

### Post by overdrank on 2009-03-14
Did you also try the command given on the instructions ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by OrangeCrate on 2009-03-14
Review these installation instructions. Particularly the part about adding the key:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by nnjond on 2009-03-14
Thanks for your interest. I've done that now, but no third party apps have appeared in add & remove

---

### Post by nnjond on 2009-03-14
"Add Medibuntu to your sources.list, as well as its GPG key to your keyring. Make sure to use the correct sources.list that corresponds to your current distribution."

Sorry. Don't know what my key ring is or how to add to it?

---

### Post by OrangeCrate on 2009-03-14
> **nnjond said:**
> "Add Medibuntu to your sources.list, as well as its GPG key to your keyring. Make sure to use the correct sources.list that corresponds to your current distribution."

Sorry. Don't know what my key ring is or how to add to it?

I just gave you the instructions on how to do this. Did you read the link I provided?

---

### Post by nnjond on 2009-03-14
Thanks for your help.As i understand it; i must issue command 3 commands to install 3rd party apps on my pc.

1. sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

2.sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

3.sudo apt-get install libdvdcss2

This i have done but no apps appear in the 3rd party "add & remove"

---

### Post by philinux on 2009-03-14
> **nnjond said:**
> Thanks for your help.As i understand it; i must issue command 3 commands to install 3rd party apps on my pc.

1. sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

2.sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

3.sudo apt-get install libdvdcss2

This i have done but no apps appear in the 3rd party "add & remove"

You are quite correct they do not appear under 3rd party. But they are there nevertheless in synaptic. Open synaptic then click the origin tab. You'll see all the medibuntu packages. Personally I never did care much for add/remove. Even as a newbie I preferred using synaptic.

---

### Post by overdrank on 2009-03-14
> **nnjond said:**
> Thanks for your help.As i understand it; i must issue command 3 commands to install 3rd party apps on my pc.

1. sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

2.sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

3.sudo apt-get install libdvdcss2

This i have done but no apps appear in the 3rd party "add & remove"

In add and remove you will see Show: that drop down menu select all available applications.

---

### Post by presence1960 on 2009-03-14
> **nnjond said:**
> hi, Ive tried to install medibuntu but it has not gone smoothly. Ive been hit by so much jargon i don,t know what to do! It begins with my command:

nnjond@nnjond-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
[sudo] password for nnjond: 
--2009-03-14 10:54:56--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 230         --.-K/s   in 0s      

2009-03-14 10:54:56 (25.7 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]

nnjond@nnjond-laptop:~$ 


But when i open add and remove i get...


W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783



What,s going on?

In terminal :
```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Here is the page to reference : [http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

---

### Post by philinux on 2009-03-14
> **overdrank said:**
> In add and remove you will see Show: that drop down menu select all available applications.

Unfortunately not all packages appear in add/remove even selecting all. e.g. acroread

---

### Post by nnjond on 2009-03-14
Thanks for your help. I can see a sequence of medibuntu pakages in synaptic manager; How does that enable me use the apps?

---

