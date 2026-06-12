---
title: "WiFi on Asus Transformer T100"
date: 2015-11-30
forum: Networking &amp; Wireless
---

### Post by Gordonbp531 on 2015-11-30
I have an Asus Transformer T100 currently running Windows 10.
It has a Broadcom WiFi adapter that Ubuntu 15.10 doesn't see at all. (Running from Live USB - don't want to install until I get the WiFi running!)
I've tried the command ```
lspci -vvnn | grep -A 9 Network 
``` from this wiki here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")
But I get the error: ```
lspci: no such PCI access method: 9 (see "-A help" for a list)
```

I can't seem to access "-A help" - can someone advise me?

[U]Update.
[/U]
In Windows it reports the WiFi adapter as a Broadcom 802.11abgn SDIO Adapter
If I issue the command ```
lspci -vvnn
``` it doesn't list any Network adapter AT ALL.
So what's going on here?

---

### Post by slickymaster on 2015-11-30
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by brianewalsh2 on 2015-11-30
This is an ongoing struggle to get any linux distro working on this little thing. Check out this community for the most up to date help, [https://plus.google.com/communities/117853703024346186936](https://plus.google.com/communities/117853703024346186936)

---

### Post by Gordonbp531 on 2015-12-02
Doesn't seem to be a huge amount of traffic there....:(

---

### Post by slickymaster on 2015-12-02
Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by Gordonbp531 on 2015-12-02
I'll give that a try.
Err how do I run a script?

---

### Post by slickymaster on 2015-12-02
Please open a terminal window (Ctrl+Alt+T) and copy+paste the following into it and then hit 'Enter'
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```

---

### Post by Gordonbp531 on 2015-12-02
No internet! That's what I'm trying to get the WiFi working for!

If I copy the script file contents from the GitHub web page, can I put it into a file and run it? If so how?

Update.
I copied the text of the script file into a file called wirelessinfo.
I chmod'd it, and then ran ./wirelessinfo.

```
 /bin/bash^M: bad interpreter: no such file or directory 
```

I'm in the directory that contains the file and the file is definitely there, so how can I run it?

---

### Post by Gordonbp531 on 2015-12-02
OK - finally got the script to run!

wireless-info.txt file attached!

---

### Post by chili555 on 2015-12-02
> brcmfmac_sdio mmc1:0001:1: Direct firmware load for brcm/[COLOR="#FF0000"]brcmfmac43340-sdio.txt[/COLOR] failed with error -2Please see: [http://www.spinics.net/lists/linux-wireless/msg134712.html](http://www.spinics.net/lists/linux-wireless/msg134712.html)> You don't need to run windows for that, the nvram (calibration data, 
probably the MAC address and related device specific data) is stored in 
your mainboard's firmware - and exposed to userspace (under linux) via
/sys/firmware/efi/efivars/. You just need to identify the correct file
and copy it to a place where linux expects to find it 
(/lib/firmware/brcm/brcmfmac43340-sdio.txt).You seem pretty adept, but if you need specific guidance, please post back and I'll see what I can do.

---

