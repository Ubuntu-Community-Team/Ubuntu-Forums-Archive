---
title: "Who To Get WPA_Supplicant to Run"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by bobt12 on 2008-03-22
I am having trouble getting my Linksys wireless card to work with WPA. It worked just fine without security and with WEP. I have wpa_supplicant installed even tried reinstall with synaptic. I have found that I have no wpa_supplicant.conf file. I ran gedit wpa_supplicant.conf and it can up blank.
   Could someone walk me through the procedure to get this to work?

---

### Post by kevdog on 2008-03-22
You need to create the wpa_supplicant.conf file in the /etc directory.  Here is a post of mine telling you how to populate the file:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by bobt12 on 2008-03-22
Thanks for the reply. I know enough about linux to get myself in trouble so if you can bare with me I have some stupid questions about the command.
Is this the correct starting point for me?

gksu gedit /etc/wpa_supplicant.conf

Inside the file add the following for WPA(1):

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="ESSID_IN_QUOTES"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="ASCII PSK Password in Quotes"
        pairwise=TKIP
        group=TKIP
 What exactly do I put in place of "ESSID_IN_QOUTES"
and is "ASCII PSK Password in Quotes" what I have for a password in my router?
Thanks
Bob

---

### Post by kevdog on 2008-03-22
ESSID = name of network
Password = WPA password on router

---

### Post by bobt12 on 2008-03-22
OK> I put all that into the .conf file. Now the next step is

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig <interface> up
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

Is <interface>  exatly what I should put or is interface the name of my router wireless card or name of network?

---

### Post by kevdog on 2008-03-22
What  does iwconfig show??

Its either going to be wlan0, ath0, eth1 or something like that.

---

### Post by bobt12 on 2008-03-22
It shows  wlan0   IEEE 802.11g ESSID:off/any
                        Mode:Managed Frequency:2.412 Ghz Access Point: Not-Associated
                        Bit Rate-54 Mb/s  Tx-Power:10 dBm  Sensitivity=0/3
                        RTS thr=4096 B  Fragment thr=4096 B
                        Power Management:off
                        Link Quality:0 Signal level:0 Noise level:0
                        Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
                        Tx excessive retries:0 Invalid misc:0 Missed Beacon:0

---

### Post by kevdog on 2008-03-22
So its wlan0

---

### Post by bobt12 on 2008-03-22
Now I'm stuck on 
sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf

I put ndiswrapper=wext in < > it came back with Unsupported driver ndiswrapper=wext

---

### Post by kevdog on 2008-03-22
-Dwext

---

### Post by bobt12 on 2008-03-22
I put 
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf   
 and it came back with 

Line 11: network block was not terminated properly.
Line 11: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'

---

### Post by kevdog on 2008-03-22
Please post your wpa_supplicant.conf file.  did you leave out the closing }?

---

### Post by bobt12 on 2008-03-22
It's

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
                   ssid="NOWIN"
                   scan_ssid=0
                   proto=WPA
                   key_mgmt=WPA-PSK
                   psk="Stemcells2824"
                   pairwise=TKIP
                   group=TKIP
                   }
I did forget the closing   } just added it and tried again with the same results.

---

### Post by kevdog on 2008-03-22
Interesting

can you post the line where you try to invoke wpa_supplicant

the sudo wpa_supplicant line?

Also try a simplified conf file like:

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="myssid"
   psk="mysecret"
   key_mgmt=WPA-PSK
   proto=WPA
 }

---

### Post by bobt12 on 2008-03-22
It's 
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf 

I believe that is the line you are asking about?
 Tried the simplified file you gave me with the same results.

---

### Post by kevdog on 2008-03-22
Can you put the -dd flag in your command line and try again?

---

### Post by bobt12 on 2008-03-22
Where in the command do I put that -dd?

---

### Post by kevdog on 2008-03-22
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

---

### Post by bobt12 on 2008-03-22
It looks a little better but at the end it the same.
Here is what came back
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=5):
     4e 4f 57 49 4e                                    NOWIN           
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=13): [REMOVED]
pairwise: 0x8
group: 0x8
Line 11: network block was not terminated properly.
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 11: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request

---

### Post by kevdog on 2008-03-22
What's on line 11 of the file??

---

### Post by bobt12 on 2008-03-22
Using the simplified file you gave me there is no line 11.
It's

It'sap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
ssid="myssid"
psk="mysecret"
key_mgmt=WPA-PSK
proto=WPA
}

---

### Post by kevdog on 2008-03-22
Can you do a

ls -la /etc/wpa_supplicant.conf

Also 
cat wpa_supplicant.conf

---

### Post by bobt12 on 2008-03-22
Here is what that those returned

oem@ubuntujake:~$ ls -la /etc/wpa_supplicant.conf
-rw-r--r-- 1 root root 157 2008-03-22 12:52 /etc/wpa_supplicant.conf
oem@ubuntujake:~$ ls -la /etc/wpa_supplicant.conf
-rw-r--r-- 1 root root 157 2008-03-22 12:52 /etc/wpa_supplicant.conf
oem@ubuntujake:~$ cat wpa_supplicant.conf
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="NOWIN"
        psk="Stemcells2824"
        key_mgmt=WPA-PSK
        proto=WPA
        }

---

### Post by kevdog on 2008-03-22
delete the file and try to run the command and see what debugging message you get.  Im curious about the line 11 error -- might be spaces in the file or something.

---

### Post by bobt12 on 2008-03-22
Deleted all the information in the file. Is that what you meant by delete the file?
Ran the command again here is the result

oem@ubuntujake:~$  sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Password:
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=5):
     4e 4f 57 49 4e                                    NOWIN           
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=13): [REMOVED]
pairwise: 0x8
group: 0x8
Line 11: network block was not terminated properly.
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 11: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request

---

### Post by kevdog on 2008-03-22
No remove the file and dont replace it!!

---

### Post by bobt12 on 2008-03-22
What I did is run
gedit wpa_supplicant.conf

When the file opened I deleted everything in it. Then hit save. Then closed it.
Then I ran the command in the previous post.
Is that correct?

---

### Post by kevdog on 2008-03-22
sudo rm /etc/wpa_supplicant.conf

Then run the command again.

---

### Post by bobt12 on 2008-03-22
Here is what I got now.

oem@ubuntujake:~$ sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request

---

### Post by kevdog on 2008-03-22
Ok start to add a few lines back into the file and try again.  Dont add extra spaces or lines at the end. Just add a few lines followed by the } and keep trying until you get a reasonable error.

---

### Post by bobt12 on 2008-03-22
I added two lines after network and put the }at the end and this is what I got after running the command

oem@ubuntujake:~$ sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=5):
     4e 4f 57 49 4e                                    NOWIN           
scan_ssid=0 (0x0)
Line 7: WPA-PSK accepted for key management, but no PSK configured.
Line 7: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request

---

### Post by kevdog on 2008-03-22
Just keep adding lines and see what happens.

---

### Post by bobt12 on 2008-03-22
I went back and started over and now when I do the command 
sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 
It is now doing  a scan and does not seem to stop saying resource temporarily unavailable failed to get scan results.
How do I stop this? So I can enter the next command.

---

### Post by kevdog on 2008-03-22
Take the -dd flag out

---

### Post by bobt12 on 2008-03-22
Well Thanks a lot for all your help. I'll have to revisit this at some other time. Now I'm back to where I was at the begining. Time to get away.

---

### Post by kevdog on 2008-03-22
Hmm I was thinking about this problem some,  what does the following tell you

cat /etc/network/interface | wc -l

This should give you the number of lines in the file.

---

### Post by bobt12 on 2008-03-23
Not getting anywhere with that command it says no such file or directory. Is the last command an -L or an -I.

---

### Post by kevdog on 2008-03-23
its an l -- right after k.  Do a man wc to list all the options for the wc command.

---

### Post by bobt12 on 2008-03-29
I am back at this today for a little while. I decided to start over. I removed the /etc/wpa_supplicant.conf file and then made a new one as your post shows. I got to the point of putting in the line " sudo wpa_supplicant -w -Dwet -iwlan0 -c/etc/wpa_supplicant.conf -dd". Without the " ".  
I'm getting
Selecting BSS from priority group 0
0: 00:12:17:32:17:b2 ssid='NOWIN' wpa_ie_len=26  rsn_ie_len=0 caps=0x11 skip WPA IE - GTK cipher mismatch
No suitable AP found

It then does this continually. I have to close terminal to get it to stop.

I will try that line again without the -dd and post back with the result.

---

### Post by bobt12 on 2008-03-29
OK I removed the /etc/wpa_supplicant.conf file again and then started over again. This time when I got to the line " sudo wpa_supplicant -w -Dwet -iwlan0 -c/etc/wpa_supplicant.conf -dd". Without the " ". 

I entered it without the -dd at the end and I got
ioctrl[SIOCGIWSCAN]: resource temporarily unavailable

and it keeps doing that and will not stop.

---

