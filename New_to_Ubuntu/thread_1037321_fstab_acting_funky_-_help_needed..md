---
title: "fstab acting funky - help needed."
date: 2009-01-11
forum: New to Ubuntu
---

### Post by ghostofzuul on 2009-01-11
Hi. 

Yesterday, I was successfully aided in installing a second (back-up) hard drive onto my linux box. You can follow along in this post:

[http://ubuntuforums.org/showthread.php?t=1036647](http://ubuntuforums.org/showthread.php?t=1036647)

however, since then whenever I restart my machine, I get an error message seemingly from the bios saying "A problem has been detected with your hard drive. Check the users manual..."

Then when starting up, ubuntu goes into terminal mode to start, the lines went by fast so I couldn't really read it... 

ubuntu starts up fine... the back up disc is still accessible and i have no obvious problems with my os.

not sure what code i would need to post to help deduce the problem any advice would be most appreciated.

---

### Post by blueridgedog on 2009-01-11
You can view the boot messages with the command ```
dmesg
```

I am not certain about the bios message.

---

### Post by kestrel1 on 2009-01-11
If you are getting a message during POST I would suspect that the drive in question has failed SMART & may need replacing.
Are you sure this message is during POST?

---

### Post by mjheagle8 on 2009-01-11
you can also view the logs under system>administration>system logs.

---

### Post by ghostofzuul on 2009-01-11
Not sure what's relevant but here's what looks like happened last logout-login...

[  267.084859] ata1.00: status: { DRDY ERR }
[  267.084864] ata1.00: error: { UNC }
[  267.108628] ata1.00: configured for UDMA/66
[  267.124156] ata1.01: configured for UDMA/100
[  267.124200] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  267.124209] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  267.124218] Descriptor sense data with sense descriptors (in hex):
[  267.124222]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  267.124235]         02 dd 0b 00 
[  267.124241] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  267.124254] end_request: I/O error, dev sda, sector 48040704
[  267.124300] ata1: EH complete
[  267.125739] sd 0:0:0:0: [sda] 60074784 512-byte hardware sectors (30758 MB)
[  267.125788] sd 0:0:0:0: [sda] Write Protect is off
[  267.125795] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  267.125844] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  267.125907] sd 0:0:1:0: [sdb] 78125000 512-byte hardware sectors (40000 MB)
[  267.125934] sd 0:0:1:0: [sdb] Write Protect is off
[  267.125939] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  267.125981] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  267.126030] sd 0:0:0:0: [sda] 60074784 512-byte hardware sectors (30758 MB)
[  267.126057] sd 0:0:0:0: [sda] Write Protect is off
[  267.126062] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  267.129361] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  267.129472] sd 0:0:1:0: [sdb] 78125000 512-byte hardware sectors (40000 MB)
[  267.129505] sd 0:0:1:0: [sdb] Write Protect is off
[  267.129511] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  267.129555] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  466.395957] usb 2-2.3.2: USB disconnect, address 6
[  494.006855] usb 2-2.3.2: new low speed USB device using uhci_hcd and address 8
[  494.149977] usb 2-2.3.2: configuration #1 chosen from 1 choice
[  494.218994] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1f.4/usb2/2-2/2-2.3/2-2.3.2/2-2.3.2:1.0/input/input7
[  494.241773] input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1f.4-2.3.2
[  514.753239] usb 2-2.3.2: USB disconnect, address 8
[  564.272869] usb 2-2.3.2: new low speed USB device using uhci_hcd and address 9
[  564.415112] usb 2-2.3.2: configuration #1 chosen from 1 choice
[  564.479708] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1f.4/usb2/2-2/2-2.3/2-2.3.2/2-2.3.2:1.0/input/input8
[  564.507160] input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1f.4-2.3.2
[  608.271569] usb 2-2.2.1: USB disconnect, address 7
[  611.286921] usb 2-2.4: new full speed USB device using uhci_hcd and address 10
[  611.420119] usb 2-2.4: configuration #1 chosen from 1 choice
[  611.501685] scsi3 : SCSI emulation for USB Mass Storage devices
[  611.505832] usb-storage: device found at 10
[  611.505849] usb-storage: waiting for device to settle before scanning
[  616.505129] usb-storage: device scan complete
[  616.508281] scsi 3:0:0:0: Direct-Access     Lexar    JD Mercury       3000 PQ: 0 ANSI: 0 CCS
[  616.532029] sd 3:0:0:0: [sdc] 1965056 512-byte hardware sectors (1006 MB)
[  616.535051] sd 3:0:0:0: [sdc] Write Protect is off
[  616.535074] sd 3:0:0:0: [sdc] Mode Sense: 43 00 00 00
[  616.535081] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  616.549133] sd 3:0:0:0: [sdc] 1965056 512-byte hardware sectors (1006 MB)
[  616.552126] sd 3:0:0:0: [sdc] Write Protect is off
[  616.552153] sd 3:0:0:0: [sdc] Mode Sense: 43 00 00 00
[  616.552159] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  616.552181]  sdc: sdc1
[  616.558382] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[  616.558506] sd 3:0:0:0: Attached scsi generic sg3 type 0
[  623.623089] usb 2-2.2: USB disconnect, address 3
[  623.760008] usb 2-2.3.2: USB disconnect, address 9
[  628.428425] usb 2-2.3.2: new low speed USB device using uhci_hcd and address 11


thx...

---

### Post by blueridgedog on 2009-01-11
With:

[ 267.124241] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 267.124254] end_request: I/O error, dev sda, sector 48040704

Looks like the drive my have a hardware issue.

---

### Post by blueridgedog on 2009-01-11
Duplicate post...sticky fingers

---

### Post by kestrel1 on 2009-01-12
Is sda your boot drive?
If so I would look in to backing up your data & replacing the drive before it does fail, if you are getting the error during POST & startup then it looks like it is on the way out.
I think it is just a coincidence that this has happened after doing what you did to fstab.

---

### Post by ghostofzuul on 2009-01-12
> **kestrel1 said:**
> Is sda your boot drive?
If so I would look in to backing up your data & replacing the drive before it does fail, if you are getting the error during POST & startup then it looks like it is on the way out.
I think it is just a coincidence that this has happened after doing what you did to fstab.


yikes! thanks for pointing that out to me... I figured it was the (used) hard drive i just installed but indeed it looks like it's the boot drive... 

i just got this box and am just using ubuntu/linux for the first time so there's nothing on here to lose. Actually am learning a lot through simple installation of os and hard drives etc so it's not the end of the world for me.

thanks a lot for the look-out...

---

### Post by kestrel1 on 2009-01-12
I would be buying a new drive then.
In fact as a temporary solution you could change your drives around, until you get the new one & install ubuntu on the other drive, but a new drive sounds like a must.

---

### Post by ghostofzuul on 2009-01-13
> **kestrel1 said:**
> I would be buying a new drive then.
In fact as a temporary solution you could change your drives around, until you get the new one & install ubuntu on the other drive, but a new drive sounds like a must.

I went back to where I got the machine and swapped out the hard drives... i zeroed both drives out and re-partioned and reinstalled unbuntu... it worked a lot better this time b/c both drives were recognized upon installation of the OS so I didn't have to do anything...

This will be my 4th or 5th time doing the install and I must say it's a lot easier to do everything through add/remove or synaptic package manager than it is to try and do it on the command line... i'm ok with the command line stuff... but i'm not a programmer or anything... and so it's a bit daunting... i could see how if you were intimidated by computers in the first place it would be quite scary... either way though... it's good to have an understanding of the command line and i'm going to try and learn as much as i can... but still rely on the gui's for now for ubuntu...

my only real dilemma is that i still can't access the drive on my mac through my network... i can see the drive but when i click on it it doesn't give me the password dialog to sign-in. Going the other way... I can access the files on my linux box from my mac just fine so i know the network and sharing is set up properly....

now that i've got it all somewhat dialed in i'm digging it... 

my poor quicksilver was getting tired so it's nice to have some of the weight off of it with the linux box...

thanks again for everyone who added their $.02.

---

### Post by kestrel1 on 2009-01-14
Glad you got it sorted, could you do us a favour & mark the thread as solved. To do this use the Thread Tools menu at the top of this thread.
With regard to your drive sharing (MAC/Linux) I would suggest opening a new thread, as you may get a better response.
Thanks

---

