---
title: "Lenovo ThinkPad 500 GB External hard drive - 5400 rpm - Turns off"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by daniele.rosa on 2011-02-05
Dear Forum

i bought

Lenovo ThinkPad 500 GB External hard drive - 5400 rpm

and i use it on:

You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012

Everything works fine for a few minutes after i unlock the hard drive but then it goes back to lock mode.

I wonder if anyone knows about that issue and if there is a solution

Thanks
Daniele

---

### Post by mikewhatever on 2011-02-12
What exactly do you mean by 'unlock the hard drive'? Do you know what locks and unlocks it? Unrelated, but you probably shouldn't be using 10.04 yet. It's still an alpha, and will be in development till the end of April.

---

### Post by daniele.rosa on 2011-02-16
the hard drive has a hardware encryption system and a keypad to unlock
it with a code

you plug it in with a usb and then unlock it
when it is unlocked it works like a normal hard drive where you can
read and write with no encryption and ubuntu sees it and opens the
file manager
if you unplug it, it relocks right away

the problem is that after a while that i am copying the hard drive
re-locks itself
i suspect there is some software signal from ubuntu that disconnect it
and as soon as it is disconnected it relocks

with respect to the ubuntu version
i suppose i downloaded the wrong one :(

daniele

---

### Post by daniele.rosa on 2011-08-06
So there is no solution for this issue?

---

### Post by omelette on 2011-08-06
First off, never heard of a HD with an unlock keypad on it, so I would be very surprised if any Linux box catered specifically for it - kind of a niche market!  The only thing I can suggest is that maybe you have Power Management (System/Preferences) set to turn off the harddrive.  Long-shot given it's a USB drive, at least I presume its an external USB drive.

---

### Post by eveg on 2011-08-06
> **mikewhatever said:**
> 
Unrelated, but you probably shouldn't be using 10.04 yet. It's still an alpha, and will be in development till the end of April.
 
he meant 11.04?
 
10.04 is the current stable lts(long term support release).
which might be a good thing to try, unless you just want to play with the new release and help get the bugs out of it. 
 
omlette's solution sounds like a good thing to try. but you may also want to back up your data and install (switch to) 10.04 --- of course, if you're backing up data and your drive shuts down...

---

### Post by daniele.rosa on 2011-08-07
thanks for the replies

i am using now Ubuntu 10.10 the Maverick Meerkat

and the system unmount the hard drive when i am copying data

this is in the messages:

Aug  7 17:27:02 daniele-laptop kernel: [149557.136143] usb 1-3: USB disconnect, address 30
Aug  7 17:27:02 daniele-laptop kernel: [149557.136208] sd 14:0:0:0: Device offlined - not ready after error recovery
Aug  7 17:27:02 daniele-laptop kernel: [149557.136239] sd 14:0:0:0: [sdc] Unhandled error code
Aug  7 17:27:02 daniele-laptop kernel: [149557.136242] sd 14:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Aug  7 17:27:02 daniele-laptop kernel: [149557.136247] sd 14:0:0:0: [sdc] CDB: Write(10): 2a 00 2f 1a 03 17 00 00 f0 00
Aug  7 17:27:02 daniele-laptop kernel: [149557.136271] lost page write due to I/O error on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.136281] lost page write due to I/O error on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.136289] lost page write due to I/O error on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.136296] lost page write due to I/O error on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.136303] lost page write due to I/O error on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.136310] lost page write due to I/O error on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.136317] lost page write due to I/O error on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.136324] lost page write due to I/O error on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.136331] lost page write due to I/O error on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.136338] lost page write due to I/O error on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.139880] sd 14:0:0:0: [sdc] Unhandled error code
Aug  7 17:27:02 daniele-laptop kernel: [149557.139884] sd 14:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Aug  7 17:27:02 daniele-laptop kernel: [149557.139889] sd 14:0:0:0: [sdc] CDB: Write(10): 2a 00 2f 1a 04 07 00 00 f0 00
Aug  7 17:27:02 daniele-laptop kernel: [149557.210547] 
Aug  7 17:27:02 daniele-laptop kernel: [149557.300407] JBD: Detected IO errors while flushing file data on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.308712] JBD: Detected IO errors while flushing file data on sdc1
Aug  7 17:27:02 daniele-laptop kernel: [149557.344757] 
Aug  7 17:27:02 daniele-laptop kernel: [149557.344858] 
Aug  7 17:27:03 daniele-laptop kernel: [149557.833625] 
Aug  7 17:27:03 daniele-laptop kernel: [149557.930801] __journal_remove_journal_head: freeing b_committed_data

---

