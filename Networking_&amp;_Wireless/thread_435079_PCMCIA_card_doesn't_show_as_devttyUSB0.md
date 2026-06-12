---
title: "PCMCIA card doesn't show as /dev/ttyUSB0"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by rstoya05-lx on 2007-05-06
Hi, 

I'm trying to get a data card (Sierra Wireless AirCard 875) with Cingular plan working on my Ubuntu version 6.10. I found some instructions:
[http://ubuntuforums.org/showthread.php?t=320557](http://ubuntuforums.org/showthread.php?t=320557)

According to them when I insert the card I should see a /dev/ttyUSB0 device. But I don't. Can anyone explain what's going on? Some more information follows...

I did a recursive listing of directories under /dev before and after inserting the card in the PCMCIA slot. I see two new directories showing up:

```
/dev/bus/usb/006:
total 0
crw-rw-r-- 1 root root 189, 640 2007-05-06 15:31 001
crw-rw-r-- 1 root root 189, 641 2007-05-06 15:32 002

/dev/bus/usb/007:
total 0
crw-rw-r-- 1 root root 189, 768 2007-05-06 15:31 001

```

Also, I see the following output in /var/log/messages:

```
May  6 15:31:57 kernel: [17183018.544000] pccard: CardBus card inserted into slot 0
May  6 15:31:58 kernel: [17183018.844000] PCI: Enabling device 0000:16:00.0 (0000 -> 0002)
May  6 15:31:58 kernel: [17183018.844000] ACPI: PCI Interrupt 0000:16:00.0[A] -> GSI 16 (level, low) -> IRQ 169
May  6 15:31:58 kernel: [17183018.844000] ohci_hcd 0000:16:00.0: OHCI Host Controller
May  6 15:31:58 kernel: [17183018.844000] ohci_hcd 0000:16:00.0: new USB bus registered, assigned bus number 6
May  6 15:31:58 kernel: [17183018.844000] ohci_hcd 0000:16:00.0: irq 169, io mem 0xe6000000
May  6 15:31:58 kernel: [17183018.928000] usb usb6: configuration #1 chosen from 1 choice
May  6 15:31:58 kernel: [17183018.928000] hub 6-0:1.0: USB hub found
May  6 15:31:58 kernel: [17183018.928000] hub 6-0:1.0: 1 port detected
May  6 15:31:58 kernel: [17183019.032000] PCI: Enabling device 0000:16:00.1 (0000 -> 0002)
May  6 15:31:58 kernel: [17183019.032000] ACPI: PCI Interrupt 0000:16:00.1[B] -> GSI 16 (level, low) -> IRQ 169
May  6 15:31:58 kernel: [17183019.032000] ohci_hcd 0000:16:00.1: OHCI Host Controller
May  6 15:31:58 kernel: [17183019.032000] ohci_hcd 0000:16:00.1: new USB bus registered, assigned bus number 7
May  6 15:31:58 kernel: [17183019.032000] ohci_hcd 0000:16:00.1: irq 169, io mem 0xe6001000
May  6 15:31:58 kernel: [17183019.116000] usb usb7: configuration #1 chosen from 1 choice
May  6 15:31:58 kernel: [17183019.116000] hub 7-0:1.0: USB hub found
May  6 15:31:58 kernel: [17183019.116000] hub 7-0:1.0: 1 port detected
May  6 15:32:00 kernel: [17183021.340000] ohci_hcd 0000:16:00.0: wakeup
May  6 15:32:01 kernel: [17183022.484000] ohci_hcd 0000:16:00.0: wakeup
May  6 15:32:02 kernel: [17183022.868000] usb 6-1: new full speed USB device using ohci_hcd and address 2
May  6 15:32:02 kernel: [17183023.080000] usb 6-1: configuration #1 chosen from 1 choice

```

If the above output means the card is property recognized then which device is the card? There are 2 new files under /dev/bus/usb/006 and one under /dev/bus/usb/007. My hardware is a Lenovo T60 laptop.

---

### Post by jmarshall on 2007-05-06
I had the same problem until I found [http://tirania.org/blog/archive/2007/Feb-21-2.html](http://tirania.org/blog/archive/2007/Feb-21-2.html) .  In short, do the following as root:

    modprobe usbserial vendor=0x1199 product=0x6820

You will know success by the tail of /var/log/syslog , and by the new existence of /dev/ttyUSB* .  You should then be able to "pon cingular", For help with setting that up, see 

    [http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/](http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/)

... and another page with a couple of possibly useful links:

    [http://ubuntuforums.org/showthread.php?t=320557](http://ubuntuforums.org/showthread.php?t=320557)

Good luck!

James

---

### Post by rstoya05-lx on 2007-05-06
Ok I got ahead now. I can see /dev/ttyUSB0, /dev/ttyUSB1, and /dev/ttyUSB2. The only addition is I needed both of these:

```
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x1199 product=0x6820 

```

I also followed this:
[http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/](http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/)

When I type 'pon cingular' I don't get any errors (the /dev/ttyUSB0) is there now but also nothing happens. What should I actually see (or do) after typing this command? I'm currently connected on a regular wireless connection. I don't that if that matters.

---

### Post by Grayscale on 2007-05-11
I think the "cingular" part in the command pon cingular is specifying a configuration file which tells what host to connect to, what username/pass and all of that.   I think its in /etc/ppp/peers.  I followed a guide to get GPRS internet connection working on my phone and it used the pon command as well.  But yeah, you'll have to make that cingular file.

Follow this guide on making it:

[http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/](http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/)

---

### Post by rstoya05-lx on 2007-05-12
Ok, I suggest making sure the card works first by trying it on Windows for example. It turned out my SIM card was bad. I am going to the Cingular store to have that sorted out.

---

### Post by rstoya05-lx on 2007-05-12
Despite what the Cingular guy told me the SIM card wasn't bad. It was just suspended (for reasons not explained). In any case I got this working as well now. 

I've a Sierra Wireless Aircard 875, a Cingular data plan and Ubuntu 6.10.

---

### Post by nicpottier on 2007-05-16
I've been trying to get this working as well.

I think the hardware side is down pat, but I'm still having trouble getting an actual connection.


I've been wrestling with this all night and haven't gotten it quite working yet. 

Couple questions:
  - what version of the sierra driver are you using?  I downloaded the latest from their website (1.0.6) but that doesn't seem to help
  - are you using their PPP scripts or the ubuntu ones?

When I run pon, /var/log/messages shows:

May 16 20:04:05 lagom pppd[6422]: pppd 2.4.4 started by nicp, uid 1000
May 16 20:04:06 lagom chat[6426]: abort on (BUSY)
May 16 20:04:06 lagom chat[6426]: abort on (NO CARRIER)
May 16 20:04:06 lagom chat[6426]: abort on (VOICE)
May 16 20:04:06 lagom chat[6426]: abort on (NO DIALTONE)
May 16 20:04:06 lagom chat[6426]: abort on (NO DIAL TONE)
May 16 20:04:06 lagom chat[6426]: abort on (NO ANSWER)
May 16 20:04:06 lagom chat[6426]: abort on (DELAYED)
May 16 20:04:06 lagom chat[6426]: send (ATZ^M)
May 16 20:04:06 lagom chat[6426]: expect (OK)
May 16 20:04:06 lagom chat[6426]: ATZ^M^M
May 16 20:04:06 lagom chat[6426]: OK
May 16 20:04:06 lagom chat[6426]:  -- got it 
May 16 20:04:06 lagom chat[6426]: send (AT+CGDCONT=1,"IP","ISP.CINGULAR"^M)
May 16 20:04:06 lagom chat[6426]: expect (OK)
May 16 20:04:06 lagom chat[6426]: ^M
May 16 20:04:06 lagom chat[6426]: AT+CGDCONT=1,"IP","ISP.CINGULAR"^M^M
May 16 20:04:06 lagom chat[6426]: OK
May 16 20:04:06 lagom chat[6426]:  -- got it 
May 16 20:04:06 lagom chat[6426]: send (ATDT*99***1#^M)
May 16 20:04:07 lagom chat[6426]: expect (CONNECT)
May 16 20:04:07 lagom chat[6426]: ^M
May 16 20:04:07 lagom chat[6426]: ATDT*99***1#^M^M
May 16 20:04:07 lagom chat[6426]: CONNECT
May 16 20:04:07 lagom chat[6426]:  -- got it 
May 16 20:04:07 lagom chat[6426]: send (\d)
May 16 20:04:08 lagom pppd[6422]: Serial connection established.
May 16 20:04:08 lagom pppd[6422]: Using interface ppp0
May 16 20:04:08 lagom pppd[6422]: Connect: ppp0 <--> /dev/ttyUSB0
May 16 20:04:15 lagom pppd[6422]: Could not determine remote IP address: defaulting to 10.64.64.64
May 16 20:04:15 lagom pppd[6422]: local  IP address 166.214.141.195
May 16 20:04:15 lagom pppd[6422]: remote IP address 10.64.64.64
May 16 20:04:15 lagom pppd[6422]: primary   DNS address 10.11.12.13
May 16 20:04:15 lagom pppd[6422]: secondary DNS address 10.11.12.14

And my the light turns on showing connectivity, but no dice.
nicp@lagom:/etc/ppp/peers$ ping 10.11.12.13
PING 10.11.12.13 (10.11.12.13) 56(84) bytes of data.

--- 10.11.12.13 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6011ms

Wondering if my routes are set wrong, are you using the built in Network Manager?

My ifconfig:
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:166.214.141.195  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:118 (118.0 b)  TX bytes:1105 (1.0 KiB)

Would appreciate any tips you have for debugging this, this is my last hurdle to having Feisty up to the same level of functionality as my old XP setup.

---

### Post by jedisurfer on 2007-11-29
Did you ever get it to connect?  I have the same problem with the remote connection being 10.64.64.64 but nothing really being connected.

Thx....

---

### Post by mikemike on 2008-01-09
I was having the same problem as nicpottier mentioned above.  My blue light was coming on, but I still wasn't able to browse the internet.  I'm fairly new to Linux and I don't understand much coding, but I'm pretty good at following directions.  After a lot of searching and trial and error, I figured out a solution that seems to work for me.  After following ITGuys directions with only one change.  I had to use WAP.Cingular instead of ISP.Cingular in the second file that he tells you to create.  After typing pon cingular, my 3G light turns blue, but the DNS says 10.11.12.13 and 10.11.12.14.  In the terminal window, Just type:

sudo route del default gw 0.0.0.0
sudo route del -host 10.64.64.64

Then unplug the card, plug it in again.  When the 2G or 3G light turns orange.  Type pon cingular and it should connect now.  I don't understand the specifics to why this works, but it has been working consistently for me.  I am using Ubuntu 7.10 Gutsy Gibon with a Compaq Evo N610c laptop. 1.8 ghz processor.

update: The trick I posted above didn't work for me today.  It may have just been coincidence the other day.  I'm back to the drawing board.  I can't figure out why sometimes it connects and sometimes it doesn't.  If anyone else has any insight, please let me know.

another update:  I'm still trying to get this to work consistently.  Sometimes it connects, sometimes it doesn't.  But I can't figure out why.  In the meantime, I found another temporary work-around that seems to help.  I found the command killall pppd.  This will disconnect the modem without having to unplug it.  Then I run pon cingular again.  I do this repeatedly until I get a connection.  I also have a work-around to know if I'm connected.  I open another terminal window and type sudo tail -f /var/log/messages.  This will display messages about the connection.  Once the last 2 lines read anything other than 10.11.12.13 and 10.11.12.14.  It's usually connected.

If someone has found a real solution and can explain it to me very slowly, please let me know.

---

### Post by joiningtheherd on 2008-01-11
I'm having a very frustrating issue with this card and the pppd system.  I've never used a ppp connection under linux, and I don't know how it works.  The driver seems to be working as a device node is created for my wireless card.  The device is also apparently obtaining an IP and DNS servers but I could be wrong.  Here's the pertinent bits of 'tail /var/log/messages' for the past three connections.

```
Jan 11 17:59:55 trevor-laptop pppd[8978]: CHAP authentication succeeded
Jan 11 17:59:55 laptop pppd[8978]: CHAP authentication succeeded
Jan 11 18:00:00 laptop pppd[8978]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 11 18:00:00 laptop pppd[8978]: local  IP address 166.128.16.181
Jan 11 18:00:00 laptop pppd[8978]: remote IP address 10.64.64.64
Jan 11 18:00:00 laptop pppd[8978]: primary   DNS address 209.183.48.11
Jan 11 18:00:00 laptop pppd[8978]: secondary DNS address 209.183.48.10
```
```
Jan 11 18:06:11 laptop pppd[9093]: CHAP authentication succeeded
Jan 11 18:06:11 laptop pppd[9093]: CHAP authentication succeeded
Jan 11 18:06:34 laptop pppd[9093]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 11 18:06:34 laptop pppd[9093]: local  IP address 166.128.221.233
Jan 11 18:06:34 laptop pppd[9093]: remote IP address 10.64.64.64
Jan 11 18:06:34 laptop pppd[9093]: primary   DNS address 10.11.12.13
Jan 11 18:06:34 laptop pppd[9093]: secondary DNS address 10.11.12.14
```
```
Jan 11 18:07:44 laptop pppd[9105]: CHAP authentication succeeded
Jan 11 18:07:44 laptop pppd[9105]: CHAP authentication succeeded
Jan 11 18:07:48 laptop pppd[9105]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 11 18:07:48 laptop pppd[9105]: local  IP address 166.128.43.116
Jan 11 18:07:48 laptop pppd[9105]: remote IP address 10.64.64.64
Jan 11 18:07:48 laptop pppd[9105]: primary   DNS address 209.183.48.11
Jan 11 18:07:48 laptop pppd[9105]: secondary DNS address 209.183.48.10
```
NOTE: The second attempt didn't connect as these are default values used for DNS.

The kernel routing table:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
```
I think it must be some sort of routing error, but not being familiar with how that works (never had issues here before) I'd love some input as to how to fix this.  In any event I'm off to find a good explanation of this system and try to fix it myself.  I think this may account for a majority of the issues users are having with this card.  I've noted several complaints about apparent connections, but not going anywhere.  Cheers.

---

### Post by mikemike on 2008-01-11
I hope you find some answers.  Please post them, if you do.

---

