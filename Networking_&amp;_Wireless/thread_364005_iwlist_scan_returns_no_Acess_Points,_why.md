---
title: "iwlist scan returns no Acess Points, why?"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by Tahir on 2007-02-17
Hello all,

I was following the instructions of this thread:

[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

and when I typed in "iwlist scan", it said "No scan results"!!!  There should be three access points but nothing is there according to "iwlist scan".

According to the following page:

[http://www.bughost.org/bugzilla/show_bug.cgi?id=170](http://www.bughost.org/bugzilla/show_bug.cgi?id=170)

it says that sometimes it returns results, sometimes not. what do I do then?

Please answer.

---

### Post by gradedcheese on 2007-02-17
you're supposed to specify the interface name, ex:

```

sudo iwlist wlan0 scan

```

Run "iwconfig" to see which interface is the WiFi interface.

---

### Post by sdide on 2007-02-17
Hey,

"# iwlist scan" Should try and scan all interfaces, if none is specified.
If you get no results, maybe your interface is not activated?
please post output from 

# iwconfig

# cat /etc/network/interfaces | grep -v ^#

---

### Post by wieman01 on 2007-02-18
Please also post the results of this:
> lshw
If you card is a PCI one, try this also:
> lspci
If it's USB, do this:
> lsusb
Just to see if your card has been recognized. And make sure that your Ethernet cable is unplugged when you scan. Ubuntu cannot handle two connections at a time...

---

### Post by Tahir on 2007-02-18
I have "solved" the problem.

If you type just "iwlist scan" a couple of times then it probably wont list anything.

If you then type "sudo iwlist scan"  (and then type in the password when prompted) then it will most likely list the networks.

I dont know why but this worked for me!!!

Thanks to everyone for their help.

-Tahir

---

### Post by gradedcheese on 2007-02-18
hmm... most iwlist/iwconfig/etc commands do need to be run with sudo.  I wonder why a simple 'iwlist' required it though.

---

### Post by Tahir on 2007-02-18
> **gradedcheese said:**
> hmm... most iwlist/iwconfig/etc commands do need to be run with sudo.  I wonder why a simple 'iwlist' required it though.

Yes,  I have just messaged weiman to tell him to change that part of his thread where he tells users to type "iwlist scan" without using sudo so that others wont suffer the same confusion

---

### Post by wieman01 on 2007-02-18
> **gradedcheese said:**
> hmm... most iwlist/iwconfig/etc commands do need to be run with sudo.  I wonder why a simple 'iwlist' required it though.
Actually it shouldn't. First time I hear this. I never use "sudo" for any of these commands as they are not supposed to require superuser rights... But I have no idea why Tahir is facing this problem.

---

### Post by Tahir on 2007-02-18
I executed the commands just now, (while connected to the Internet) 

> tahir@tahirs:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:0C:41:B3:69:AB
                    ESSID:"HomeNet"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-64 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

sit0      Interface doesn't support scanning.

tahir@tahirs:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:0D:0B:3D:A3:7C
                    ESSID:"000d0b3da37c"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-81 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:14:BF:D7:01:56
                    ESSID:"linksys_SES_57457"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-62 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:0C:41:B3:69:AB
                    ESSID:"HomeNet"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-64 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

sit0      Interface doesn't support scanning.

as you can see, the first iwlist scan was done without sudo, and it only gave me the essid of the AP I was already connected to.  The second one gave me all the APs that should appear.

This experimental evidence supports my belief.

Secondly WITHOUT sudo, iwlist scan returns output very quickly, whereas WITH sudo, it takes a very long time (about three seconds) to scan eth0 and then it returns the results.

Anyway,
Thanks

P.S My wireless works, but I am just curious about iwlist scan thats all.

---

### Post by sdide on 2007-02-19
Its not that surprising if you read the man-pages for iwlist - actually.

From "# man iwlist.

> PARAMETERS
       scan[ning]
              Give  the  list of Access Points and Ad-Hoc cells in range, and optionally a whole bunch of information about them
              (ESSID, Quality, Frequency, Mode...). The type of information returned depends on what the card supports.
              Triggering scanning is a privileged operation (root only) and normal users can only read left-over  scan  results.
              By  default,  the  way  scanning  is  done  (the scope of the scan) will be impacted by the current setting of the
              driver. Also, this command is supposed to take extra arguments to control the scanning behaviour, but this is cur&#8208;
              rently not implemented.
"

What exactly is meant by "left-over scan results" is another question.

---

### Post by wieman01 on 2007-02-19
> **sdide said:**
> Its not that surprising if you read the man-pages for iwlist - actually.

From "# man iwlist.



What exactly is meant by "left-over scan results" is another question.
Again I cannot explain this, nor can I confirm this statement. I log on to my system as unpriviledged user and have not had an issue with it yet. Anyway, learned something new today although it does not really make a difference (in my case).

---

### Post by Tahir on 2007-02-19
> **wieman01 said:**
> Again I cannot explain this, nor can I confirm this statement. I log on to my system as unpriviledged user and have not had an issue with it yet. Anyway, learned something new today although it does not really make a difference (in my case).

hmm... I cant know everything but considering what the man pages say, hmm...

---

### Post by wieman01 on 2007-02-19
> **Tahir said:**
> hmm... I cant know everything but considering what the man pages say, hmm...
That's what really confuses me. It's the first time I hear it and your case confirms that there is some truth to it, nontheless I find it hard to believe (although I believe you of course). Anyway, learned a lesson. :-)

---

### Post by Tahir on 2007-02-19
> **wieman01 said:**
> That's what really confuses me. It's the first time I hear it and your case confirms that there is some truth to it, nontheless I find it hard to believe (although I believe you of course). Anyway, learned a lesson. :-)

Yes, we both learned a lesson!  :popcorn:

---

