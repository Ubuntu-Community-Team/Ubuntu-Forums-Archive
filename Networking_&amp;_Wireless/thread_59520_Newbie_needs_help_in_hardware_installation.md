---
title: "Newbie needs help in hardware installation"
date: 2005-08-24
forum: Networking &amp; Wireless
---

### Post by ScapinVS on 2005-08-24
Hello,

now i am a complete newbie. I downloaded Ubuntu 5.04 as my first ever Linux distrubution and I now want to use it.

It works pretty well.

Houwm. One problem: How do I install hardware? How does this work? I have a modem (a MicroLink 56K PCI, which should be compatible to Linux) and I want to get it to work. I found a Debian driver on the web as a .deb file.

But what do i have to do now? Please dont point me to google, i did not found anthing helping me there.

Thank you in advance!!   :) 

Cheers,
Scapin

---

### Post by nad on 2005-08-24
I am not going to point you to google, but, you have at your fingertips the wealth of resources of ubuntu.

Please search these forums for your particular hardware and driver installation advice.

---

### Post by ScapinVS on 2005-08-24
[QUOTE=nad]I am not going to point you to google, but, you have at your fingertips the wealth of resources of ubuntu.

Please search these forums for your particular hardware and driver installation advice.[/QUOTE]

Well i did not find something that shows me how it is going from the start.
I read words like "remake kernel" etc. But i dont know anything about that at all. I've been a windows user, now i am trying to find a way to understand how all these things work under Linux.

What would be the first step to install my modem?

I built it into my computer, downloaded the .deb file, but what do i have to do now?

---

### Post by s_p_a_r_k_y on 2005-08-24
install the .deb file

However often it is best to see if the particular package is already in your repositories. Have you looked in synaptic? System->Administration->Synaptic Package manager. Then search for the package you downloaded. This is the recommended method to install any software on debian based systems as it will download any needed software to go a long with the package you selected. A mistake newbies often make it going to websites to download software, debian takes that fun out and replaces it with pure bliss as I haven't gone ot a website to download software in months but it all comes through apt.

If you can't find it in Synaptic, do this
sudo dpkg -i nameOfFile.deb

of courese you should be in the same directory as the .deb file

---

### Post by ScapinVS on 2005-08-24
Ok, thanks.

I've done that way.

It is not in Synaptic so i executed your command.

First it does that "Selecting previously...." part well. 

It goes on until: "Trying to automatically build the driver modules..."

Than it asks: "Where is the Linux source build directory that matches your running kernel?"

I dont find that directory, so it fails... 

I got the ISO for the installation downloaded at [www.ubuntu.com](www.ubuntu.com) (the 5.04 version for i386) under "Download". Are the sources and a compiler already included in that file?

The computer is not connected to the internet. I dont know what apt is, but I think it could download the source... if the computer were connected.

Sorry if these are all newbiew questions, but that is what I am....  :? 

Thank you!

---

### Post by s_p_a_r_k_y on 2005-08-24
um yo need the kernel-headers and kernel-source. These are .deb files. Usually you would use apt or Synaptic to install them but if you have no internet then try getting them from an ubuntu website ... usually the ones listed in /etc/apt/sources.list
you should be able to find the .deb file and download and install them. They need to be there before you can install your other .deb

---

