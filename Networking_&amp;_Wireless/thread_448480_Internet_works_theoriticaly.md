---
title: "Internet works theoriticaly : /"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by MaestroS on 2007-05-19
I were compiling and installing following driver: **rt2400-cvs-daily (2007051812)**

After **make install**, I used following commands:
> 
iwconfig ra0 essid ELiXiR-Elewator
iwconfig ra0 channel 11
iwconfig ra0 mode ad-hoc
ifconfig ra0 up
dhclient ra0
ifconfig ra0 10.0.34.111
ifup ra0 


after listed commands, I put once again **iwconfig**, and the results showed me, that connection is **active**, both **signal rate** and **signal level** were good : /

but! I couldn't access any site...

What is wrong ? Do I need to configure anything else ?

#edit
I'm using Ubuntu 7.04 Feisty Fawn and my card is RaLink Wireless RT2400

#edit2
Informations about my network:
[img]http://img96.imageshack.us/img96/6681/wln2he0.jpg[/img]
[img]http://img238.imageshack.us/img238/1312/wlnzb7.jpg[/img]

---

### Post by MaestroS on 2007-05-19
This is log from IWCONFIG result:

> 
lo no wireless connection
ra0 RT2400PCI ESSID: EliXiR-Elewator
Mode: Ad-hoc channel: 11 bit-rate: 11 Mb/s
RTS thr: off Fragment thr: off
Encryption key: 7868-7961-3965-6462-6833-0000-00 Security mode: restricted


cted Link quality: 72 Signal level: 31 Noise level: 0 


---

### Post by chili555 on 2007-05-19
I am wondering why you are using ad-hoc mode. Usually, if you want to connect to a router or access point and from there to the internet, you will want mode managed.

Also, these two:```
dhclient ra0
ifconfig ra0 10.0.34.111
```seem to be in conflict. dhclient implies I want any IP address you can give me. ifconfig <address> implies I will *only* take <address>. Wireless is a bit tricky to set up and if you use DHCP, you will know you are connected when you are handed an IP address. With static IP's, you will find it harder to know, because you have an IP address whether you are connected or not.

I suggest trying:```
iwconfig ra0 essid ELiXiR-Elewator
iwconfig ra0 channel 11
iwconfig ra0 mode managed
ifconfig ra0 up
dhclient ra0
ifup ra0
```Please post back and let us know.

---

### Post by chili555 on 2007-05-19
> 7868-7961-3965-6462-6833-0000-00Looks like you have a 20-character encryption key and iwconfig has thoughtfully filled in 6 more characters.

# 40 or 64 bit ASCII WEP code has 5 characters
# 40 or 64 bit HEX WEP code has 10 characters
# 128 bit ASCII WEP code has 13 characters
# 128 bit HEX WEP code has 26 characters 

Are you sure the key is correct? I am skeptical that your router and your computer will connect with 20 characters.

---

### Post by hartz on 2007-05-19
Please post the output from these commands after configuring the interface:
```

dmesg | tail -20
ifconfig -a
iwconfig
tail -20 /var/log/messages
```

---

### Post by MaestroS on 2007-05-19
The point is that I don't know what is "Key" and how to put my password: xhyj9edbh3

@up
I don't know how to post logs from Ubuntu to windows : /

---

### Post by hartz on 2007-05-19
and also:

cat /proc/net/wireless

---

### Post by hartz on 2007-05-19
I assume your Ubuntu system is not currently on the internet?

Insert a USB disk which is formatted as FAT32, which makes it easy to read and write from Windows and Linux.

Copy log files to the USB disk.

Alternative: Write the files to a CD which can be read on Windows.

---

### Post by hartz on 2007-05-19
I assume you have a passphrase on the windows side but you need a key on the Linux side.

In this case, have a look at THIS website, there is a small perl script to generate a key from a passphrase:

[http://linux-net.osdl.org/index.php/802.11](http://linux-net.osdl.org/index.php/802.11)

---

### Post by MaestroS on 2007-05-19
@up
how to use this perl script ? ; o

and tell me how to make log from each command

---

### Post by hartz on 2007-05-19
The commands were:

```
dmesg | tail -20
ifconfig -a
iwconfig
tail -20 /var/log/messages
```

To capture all their output into a file, enter them like this:

```
(
dmesg | tail -20
ifconfig -a
iwconfig
tail -20 /var/log/messages
) > /tmp/output.txt

```

Now you have a text file with all the outputs in a file called /tmp/outputs.txt

You can confirm it by entering this command:

```
cat /tmp/outputs.txt
```

Insert your USB disk

Then enter the command df

Look for something named similar to this:
/media/[COLOR="Red"]mydisk[/COLOR]

Once identified, copy the file with this command:
```
cp /tmp/outputs.txt /media/[COLOR="Red"]mydisk[/COLOR]
```

---

### Post by hartz on 2007-05-19
And follow Chilli's suggestion about managed mode.

---

### Post by MaestroS on 2007-05-19
Here you are



dmesg | tail -20 result:
> 
[   34.878619] ACPI: Power Button (FF) [PWRF]
[   34.919992] input: Power Button (CM) as /class/input/input7
[   34.925292] ACPI: Power Button (CM) [PWRB]
[   34.942175] ibm_acpi: ec object not found
[   35.035334] pcc_acpi: loading...
[   38.524903] cdrom: This disc doesn't have any tracks I recognize!
[   40.207170] ppdev: user-space parallel port driver
[   40.856129] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   40.856137] apm: overridden by ACPI.
[   41.058328] Bluetooth: Core ver 2.11
[   41.058410] NET: Registered protocol family 31
[   41.058413] Bluetooth: HCI device and connection manager initialized
[   41.058417] Bluetooth: HCI socket layer initialized
[   41.108028] Bluetooth: L2CAP ver 2.8
[   41.108035] Bluetooth: L2CAP socket layer initialized
[   41.210013] Bluetooth: RFCOMM socket layer initialized
[   41.210035] Bluetooth: RFCOMM TTY layer initialized
[   41.210037] Bluetooth: RFCOMM ver 1.8
[   43.752714] ra0: no IPv6 routers present
[   92.178037] ra0: no IPv6 routers present


ifconfig -a result:
> 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:904 (904.0 b)  TX bytes:904 (904.0 b)

ra0       Link encap:Ethernet  HWaddr 00:80:C6:E7:62:2B  
          inet addr:10.0.34.111  Bcast:10.255.255.255  Mask:255.255.255.255
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:6 dropped:6 overruns:0 carrier:0
          collisions:41 txqueuelen:1000 
          RX bytes:11988 (11.7 KiB)  TX bytes:12441 (12.1 KiB)
          Interrupt:18 Base address:0x4000 


iwconfig result:
> 
ra0       RT2400PCI  ESSID:"ELiXiR-Elewator"  
          Mode:Managed  Channel=10  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:73  Signal level:33  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0




cat /proc/net/wireless result:
> 
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 21
   ra0: 0000   73.   33     0        0      0      0      6      0        0


now any help ?

---

### Post by hartz on 2007-05-19
You can still give the perl script a shot.

Save the script as a text file.
Put the text file on a USB disk
Plug the disk into the Linux system
Run "df" to check where the disk got mounted (eg something like /media/[COLOR="Red"]mydisk[/COLOR])

Locate the file using a find command like this.
```
find /media/[COLOR="Red"]mydisk[/COLOR] | grep -i [COLOR="Magenta"]perscriptfilename[/COLOR]
```

Substitute the name you gave the script where I put [COLOR="Magenta"]perlscriptfilename[/COLOR]

Depending on how generic/cryptic a file name you used, you may get only one line or many.  You should be able to identify the file easily enough.  Substitute the [COLOR="Blue"]path[/COLOR] to the file you found in the next command

Copy the script to your /tmp folder.
```

cp /media/[COLOR="Blue"]mydisk/path/to/perlscript[/COLOR] /tmp/makekey.pl
```

You now have that script stored in /tmp with the file name makekey.pl

Check it (display the contents of the file):
```
cat /tmp/makekey.pl
```

Make the file executable.
```
chmod +rx /tmp/makekey.pl
```

Execute the script
```
/tmp/makekey.pl "My SeCrEt PaSs PhRaSe"
```

This should give you a key that you can use with ```
iwconfig ra0 key XXXXXXXXXXXXXXX
```

I have to admit that my knowldge of WiFi is limited, so, though it pains me to suggest this, if the perl script doesn't work, maybe give a GUI applet a shot.  A search through synaptic reveals kwifimanager, which I suspect will just do it.

---

