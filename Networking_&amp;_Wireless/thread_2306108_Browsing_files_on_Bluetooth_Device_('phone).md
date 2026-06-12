---
title: "Browsing files on Bluetooth Device ('phone)"
date: 2015-12-12
forum: Networking &amp; Wireless
---

### Post by jimford on 2015-12-12
I've searched for a solution to this problem, but most of the answers are old, have not received replies or unbelievably convoluted.

When trying to browse files on my 'phone from my Xubuntu 15.10 laptop, I get the error:

"Failed to launch default file browser. The specified location is not mounted. You can enter an alternate browser in service settings."

Wanting to browse a remote device is not an unusual or exotic thing to do, and I would have expected the facility to be there 'out of the box' - after all, it's mature consumer technology that many non technical people use from day to day. (Why is everything so difficult and technical with Ubuntu Bluetooth?)

I'd be grateful for some ideas, please!

Jim

---

### Post by jeremy31 on 2015-12-13
Here is a list of obex packages I have installed
```
ii  libmulticobex1                              0.23-1.2ubuntu3                                     amd64        multi-protocol cable OBEX libraryii  libobexftp0                                 0.23-1.2ubuntu3                                     amd64        object exchange file transfer library
ii  libopenobex1                                1.5-2.1                                             amd64        OBEX protocol library
ii  obex-data-server                            0.4.6-0ubuntu2                                      amd64        D-Bus service for OBEX client and server side functionality
ii  obexd-client                                0.46-1ubuntu7                                       amd64        D-Bus OBEX client
ii  obexfs                                      0.11-1.1                                            amd64        mount filesystem of ObexFTP capable devices
ii  obexftp                                     0.23-1.2ubuntu3                                     amd64        file transfer utility for devices that use the OBEX protocol
ii  obexpushd                                   0.11.2-1                                            amd64        program for receiving files via Bluetooth or IRDA

```

In Ubuntu 14.04 with the default bluetooth manager I can browse the files of my old HTC Touch Pro 2 Windows phone but I get no where with my Android smartphone so I would guess it doesn't support file browsing.  It doesn't offer the option using Windows either

---

### Post by jimford on 2015-12-13
Thanks for the reply.

I've installed the files, but still can't access files on my Android 5.1.1 'phone using bluetooth.

My first reaction to seeing what you needed to do get it at least partially working for you , is  - what's the point in Ubuntu not supplying *all *the files necessary for file transfer between Ubuntu and bluetooth devices, so it works out-of-the-box, without needing to do a lot of research and extra software installation?

I repeat - why is bluetooth *so damned difficult* on Ubuntu, for a mature consumer orientated technology? Does *any* Ubuntu user have bluetooth working 100%?

Jim

---

### Post by jeremy31 on 2015-12-13
I think Android is the issue, it is not allowing a bluetooth connection to browse the file system, Ubuntu might not allow a bluetooth connected device to browse its file system either, I haven't tried.

My bluetooth works with A2DP headphones, mice, and I can transfer and receive files from my android smartphone.  I don't have a bluetooth printer so I can't test that.

---

### Post by jimford on 2015-12-14
> **jeremy31 said:**
> I think Android is the issue, it is not allowing a bluetooth connection to browse the file system, Ubuntu might not allow a bluetooth connected device to browse its file system either, I haven't tried.
<snip>
[quote] I can transfer and receive files from my android smartphone..

I'm confused! So you *can* send and receive files between your Android 'phone and Ubuntu system, in spite of not being able to browse files on the 'phone?

I can send files from my Xubuntu laptop to my Android 'phone, but I can't send files from my 'phone to my Xubuntu laptop.

Jim

---

### Post by jeremy31 on 2015-12-14
File receiving in bluetooth is initially disabled but with obexftp installed you can search for "Personal File Sharing" and enable "Receive files over bluetooth" in Ubuntu.  If you have Blueman installed, you can right click on the Blueman icon and go into "Local Services" and enable

---

### Post by jimford on 2015-12-14
I'm beginning to lose the will to do this. It seems obvious to me that the Ubuntu/Xubuntu/Kubuntu developers actually don't want users to use bluetooth, so they've made it as complicated and convoluted as possible.

I don't use W7 very often (only for Photoshop), but it wouldn't surprise me if it's basically  a 'one-click' job to transfer files either way with bluetooth and an Android 'phone!

Jim

---

### Post by jeremy31 on 2015-12-14
I don't use the bluetooth transfer often as using a USB cable is faster and I can browse the files on the android with Ubuntu or Windows.
The xda developer forum would be the place to look to see if someone has enabled browse files over bluetooth in android

---

### Post by jeremy31 on 2015-12-18
I am going to see if this works
[https://play.google.com/store/apps/details?id=com.estrongs.android.pop&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5lc3Ryb25ncy5hbmRyb2lkLnBvcCJd](https://play.google.com/store/apps/details?id=com.estrongs.android.pop&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5lc3Ryb25ncy5hbmRyb2lkLnBvcCJd)

---

### Post by jeremy31 on 2015-12-18
> **jeremy31 said:**
> I am going to see if this works
[https://play.google.com/store/apps/details?id=com.estrongs.android.pop&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5lc3Ryb25ncy5hbmRyb2lkLnBvcCJd](https://play.google.com/store/apps/details?id=com.estrongs.android.pop&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5lc3Ryb25ncy5hbmRyb2lkLnBvcCJd)

That is what it takes to be able to browse files on an Android phone with Blueman as I could not find the option in the normal bluetooth manager

---

