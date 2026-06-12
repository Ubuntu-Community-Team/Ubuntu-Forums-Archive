---
title: "Just getting started - Problem with WiFi"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by Philosborn on 2008-07-14
Hy people - My first time here...

I've had this self-contained bootable Ubuntu 7.10 DVD sitting around since LOSCON and finally booted from it on my HP Pavilion dv2416us Entertainment Notebook PC, which came with (yech!) Vista on Saturday... 

The bootup went fine, and altho I've never actually used Linux, I do have many years of experience with Windose 3.0 to Vista, plus about as much time on my Amigas, so OS's are not generally scary to me.

Then I went to a party that night where I knew a Linux guru hung out, and he checked the system a little and gave me a CLI sequence to enter the name of the local WiFi and log in.  Note that I do not have ANY internet access from home, relying instead on the local libraries for a high-speed connection.  So, for Ubuntu to be really useful to me, I've got to get the WiFi working.  

Here is the string he gave me:

sudo iwconfig essid "essid" , where the entry in quotes would be the library network name.

So, here is what I got yesterday at the library in my last session attempt to debug:

ubuntu@ubuntu:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
ubuntu@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ sudo iwconfig essid
essid     No such device

ubuntu@ubuntu:~$ sudo iwconfig essid "essid"
Error for wireless request "Set ESSID" (8B1A) :
    too few arguments.
ubuntu@ubuntu:~$ sudo iwconfig essid "OCPL WiFi"
iwconfig: unknown command "OCPL WiFi"
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$

Any clue as to what I'm doing wrong?  Note that "OCPL WiFi" is the name provided by the library docs, and I don't have any problem getting online in the Vista mode on the same machine.

Fortunately, both Vista and Ubuntu recognize the USB card, so I was able to get the info from the Ubuntu session over to the Vista side.

So far, BTW, apart from the technical problem, I find Ubuntu much quicker than Vista, even running from the DVD.  At least the little search dog from XP is gone from Vista, altho I had plans for that little dog, involving heat and smoke and hot sauce.

Thanks for any help

BTW, how do I turn off the unwanted smilies???

---

