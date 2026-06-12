---
title: "Cannot Connect; Errors using Ubuntu 6.06 network-admin for Gateway 2005 laptop"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by newagelink on 2013-10-23
Hello,

I'm trying to use Ubuntu 6.06, and then upgrade as far as I can, on a Gateway laptop purchased in 2005. However, I have not been able to connect to my home network. Entering 'network-admin' from the terminal, or selecting System > Administration > Networking, I enter my wireless network details, and cannot connect, i.e. "Firefox can't find the server at ..."

When using the terminal network-admin command, the following errors are output:
```
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `parent != NULL' failed
** (network-admin:5125): CRITICAL **: gst_xml_element_find_first: assertion `node != NULL' failed
```
(Yes, I counted -- that parent error is produced seventy-two times before the final node error!)

What is the meaning of this? What is its resolution? My network uses "WPA-PSK [TKIP] + WPA2-PSK [AES]" security, which I think means devices can connect under either security mode: Is the passphrase to be entered in hexadecimal or ASCII (the two choices here for network-admin)? I have tried both and have been unsuccessful. I have also used [this WPA key calculation tool]("http://jorisvr.nl/wpapsk.html") after unsuccessfully trying the ASCII passphrase input, trying to convert instead to a hexadecimal key. My next attempt would be to try changing my network passphrase to something simpler and trying again.

What distribution should I try for this old laptop, if not the now-obsolete Ubuntu 6.06 LTS (Dapper Drake)? (Again, I was intending to use the Update Manager once connected to the internet.)

I have not been able to use the latest Ubuntu software for two reasons: One version of Ubuntu 12.04.2 Desktop tells me the hardware is incompatible with the kernel, if I recall the boot-up error message correctly. So I try downloading the 32-bit version (assuming I accidentally got the 64-bit version), thinking perhaps that is compatible with this hardware, but I cannot burn it to disc: It is larger than 700 MB, and I only have access to a CD-R/CD-RW drive, so I can't burn it to a DVD-R.

Thank you for your time.

---

### Post by TheFu on 2013-10-23
Recent Ubuntu's have had PAE kernels which are incompatible with your CPU.  You'll need the "alternate" install CD to use Ubuntu.

I can't help the proxy thing. sorry.  If you list the exact ISP, someone else using it might be able to help. Is the connection cable, DSL, wifi, wi-max ... fibre?

---

### Post by newagelink on 2013-10-23
I've been trying to connect wirelessly (wifi). The monitor's shorted out on this laptop, so I've got it connected to an external monitor in a room other than where the router is, so an ethernet cable isn't possible without moving the external monitor along with the laptop (which I can't do, either). I'm not sure why the Internet Service Provider is relevant, but it's Comcast, or perhaps "xfinity", if that's a different company ...

Someone in #ubuntu at freenode.net suggested I use Lubuntu, so I've downloaded a copy of lubuntu-13.10-desktop-i386.iso -- will this work? or is there an 'alternate' install CD I should use even for Lubuntu?

---

### Post by wildmanne39 on 2013-10-23
With that old of ubuntu version it will most likely be very hard to get wifi to work for lack of drivers, I doubt many people even remember how to get that version to connect.

I suggest that you just do a fresh install of lubuntu because it is the easiest on resources then if you have trouble connecting post back.

Also it would be very slow and end up in frustration updating over a network and you should never use wifi to update to a new release.
Thanks

---

### Post by mörgæs on 2013-10-23
If you still have some version of Ubuntu installed (even an obsolete one) please run

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags.

---

