---
title: "Mounting Issues"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by jackbusch on 2009-03-28
Hi
I'm tying to mount my OS X Install DVD (running a macbook 2,1) and I get this error:
"Cannot mount volume
"Invalid mount option when attempting to mount the volume..."
And then a little later:

"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken"




Also, I get this 
```

jakc@jakc-laptop:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       33168   266214824   af  Unknown
/dev/sda3   *       33185       36952    30263672   83  Linux
/dev/sda4           36952       38914    15755859+  82  Linux swap / Solaris
jakc@jakc-laptop:~$ 



```

---

### Post by cariboo on 2009-03-28
Could you post the output of:

```
dmesg | tail -n10
```

when you insert the dvd, in your next post.

Jim

---

### Post by Gadgetier16 on 2009-04-08
i have the same problem, and would like to see the answer to this thread
I use a PowerBook G4 with Ubuntu.

---

### Post by jackbusch on 2009-04-09
Unfortunately, I never figured it out. My hard drive failed and I just installed from scratch, which, as far as I know, solved (or mooted) the problem, possibly because I upgraded to Jaunty Beta.

---

### Post by Gadgetier16 on 2009-04-09
Are you saying that upgrading to jaunty solved the problem and is capable of mounting all forms of CD's/DVD's/ and other formats?

---

### Post by jackbusch on 2009-04-09
I actually haven't tried using a DVD, except for the DVD that I burned in order to install Jaunty in the first place. When I was having issues, however, I was having trouble mounting partitions on my internal HD and getting the same error message and now I have no problems doing that.

I can try mounting a DVD later tonight and tell you what happens.

---

### Post by Gadgetier16 on 2009-04-11
that would be helpful thanks, 
i am running intrepid on my g4 powerbook, and wished to switch back to Tiger OS for school. but as you did I recieved the same mounting error. If upgrading allow for better recognition and proper mounting than thats what I need to find out.

Thanks

---

### Post by cariboo on 2009-04-12
Could someone open an Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n10
```

after the DVD is inserted into the drive, and paste the output in a post so that we can see what if any error messages are displayed.

I have a feeling I've seen the error before, but I can't remember where I saw it.

Jim

---

### Post by Gadgetier16 on 2009-04-12
after the install cd(OSX Tiger) is put in then the error, 

the result of code
dmesg | tail -n10

i get...

[  252.729524] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  256.669953] NET: Registered protocol family 10
[  256.671112] lo: Disabled Privacy Extensions
[  256.672020] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  263.597234] wlan0: no IPv6 routers present
[ 2731.236984] conservative governor failed, too long transition latency of HW, fallback to performance governor
[ 2735.862892] conservative governor failed, too long transition latency of HW, fallback to performance governor
[ 2744.059603] conservative governor failed, too long transition latency of HW, fallback to performance governor
[ 4292.736279] UDF-fs: No partition found (1)
[ 4292.788279] ISOFS: Unable to identify CD-ROM format.

---

### Post by cariboo on 2009-04-12
I have G4 installation & Recovery disks, they aren't being read at all, so that's no help. The only thing I can suggest is to install the udftools package and see if that helps. You can use Synaptic Package Manager to install udftools.

Jim

---

### Post by jackbusch on 2009-04-12
Hi, sorry this took so long. I just tried mounting in Jaunty and same deal as before.

here's what I get

```
[  222.206359] wlan0: RX ReassocResp from 00:1e:2a:50:4a:12 (capab=0x431 status=0 aid=7)
[  222.206365] wlan0: associated
[  226.198303] wlan0: deauthenticated
[  232.288012] wlan0: authenticate with AP 00:1e:2a:50:4a:12
[  232.290390] wlan0: authenticated
[  232.290399] wlan0: associate with AP 00:1e:2a:50:4a:12
[  232.292775] wlan0: RX AssocResp from 00:1e:2a:50:4a:12 (capab=0x431 status=0 aid=7)
[  232.292780] wlan0: associated
[  379.124264] UDF-fs: No partition found (1)
[  379.238428] ISOFS: Unable to identify CD-ROM format.

```

---

### Post by Gadgetier16 on 2009-04-19
i installed udftools and am haveing trouble following the cryptic instructions i find on the forums. Do you know a link to which explains the package?

---

