---
title: "Help with SCSI tape drive"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by AndyInNYC on 2009-02-08
I just bought a $16 Adaptec AHA-2940UW SCSI card (I remember when thsese were $200+) to attach the STD224000N (Seagate Python 12/24 tape drive) I've had in storage attached to a Dell PowerEdge 2300 server.  The drive is now attached to my small home server.

The drive/card is correctly recognized during the boot process.  I have configured the speed down to 5 MB/s (the slowest speed) after lots of other interim settings and attempts (lowering the speed didn't change any of the problems, however - I've just read that this is helpful with old tape drives).

mt -f /dev/st0 status returns

SCSI 2 tape drive:
File number=0, block number=-1, partition=0.
Tape block size 512 bytes. Density code 0x25 (DDS-3).
Soft error count since last status=0
General status bits on (1010000):
 ONLINE IM_REP_EN

any time I try to write/read to the drive I get read/write errors.  I believe that the drive actually does work, so I'm inclined to believe in a configuration error rather than that it has simply died.

If anyone is using this drive, I'd love to know what dip switch settings are being used.

Device Manager shows the drive as a SCSI Device, but I believe it is being recognized as a 'generic' device.

I'm sure there is a ton of additional info I could provide if I knew how.  Let me know what I should post and how to do it if you can help fill in my blanks and get this device running.

thanks so much, in advance,

Andrew

---

### Post by blueridgedog on 2009-02-08
I have never seen the ability to mount a tape drive as a partition.  I have always used the mt and tar commands to access tape drives.  Take a look at this tutorial:

[http://www.cyberciti.biz/faq/linux-tape-backup-with-mt-and-tar-command-howto/](http://www.cyberciti.biz/faq/linux-tape-backup-with-mt-and-tar-command-howto/)

Can you access the drive with mt? 

```
mt -f /dev/st0 rewind
```

---

### Post by AndyInNYC on 2009-02-08
Thanks for your reply.

I'm not trying to mount the drive.

As my post indicated, mt -f /dev/st0 status does return a 'good' response

mt -f /dev/st0 rewind returns:

/dev/st0: Input/output error

which isn't so good.

This actually pleases me - if all worked correctly but I still couldn't write/read then it would actually be the read/write heads as opposed to some configuration error.

Any other thoughts out there?

Andrew

---

### Post by blueridgedog on 2009-02-08
My bad on the mount, I miss-read your original post.  It has been so long since I used a tape under *nix that I am having trouble recalling some of the trouble shooting steps.  

One thing is to take a look at /var/log/messages after you try the rewind command:

```
tail /var/log/messages
```

---

### Post by AndyInNYC on 2009-02-08
OK, here's the results of tail /var/log/messages:

root@SERVER:~# tail /var/log/messages
Feb  8 19:37:46 SERVER -- MARK --
Feb  8 19:57:46 SERVER -- MARK --
Feb  8 20:17:46 SERVER -- MARK --
Feb  8 20:37:46 SERVER -- MARK --
Feb  8 20:48:20 SERVER kernel: [91875.976000] st0: Sense Key : Hardware Error [c                 urrent]
Feb  8 20:48:20 SERVER kernel: [91875.976000] st0: Add. Sense: Internal target f                 ailure
Feb  8 20:48:20 SERVER kernel: [91875.984000] st0: Sense Key : Hardware Error [c                 urrent]
Feb  8 20:48:20 SERVER kernel: [91875.984000] st0: Add. Sense: Internal target f                 ailure
Feb  8 21:17:46 SERVER -- MARK --
Feb  8 21:37:46 SERVER -- MARK --
root@SERVER:~#


Does this help?

Andrew

---

### Post by blueridgedog on 2009-02-08
My first approach would be to verify that the controller is SCSI ID 7 and that the drive is something else and that the drive jumpered for termination or that the cable has a terminator.

You should be able to get the id's with:

```
cat /proc/scsi/scsi
```

---

### Post by AndyInNYC on 2009-02-09
mt -f /dev/st0 rewind works fine'

mt -f /dev/st0 erase returns an error

/dev/st0: Input/output error

 and tail /var/log/messages returns:

Feb  9 22:23:32 SERVER kernel: [  414.564000] st0: Sense Key : Medium Error [current]
Feb  9 22:23:32 SERVER kernel: [  414.564000] st0: Add. Sense: Excessive write errors



root@SERVER:~# cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 06 Lun: 00
  Vendor: SEAGATE  Model: DAT    04106-XXX Rev: 7550
  Type:   Sequential-Access                ANSI  SCSI revision: 02
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: AMCC     Model: 9500S-8    DISK  Rev: 2.08
  Type:   Direct-Access                    ANSI  SCSI revision: 03


This is returned with dip switch 4 (MRS detect) set to ON which is the default.

Set to OFF, the same erase command returns:

root@SERVER:~# mt -f /dev/st0 erase                                             
/dev/st0: Input/output error

and tail /var/log/messages returns:

Feb  9 22:42:18 SERVER kernel: [  291.892000] st0: Sense Key : Medium Error [current]
Feb  9 22:42:18 SERVER kernel: [  291.892000] st0: Add. Sense: Excessive write errors
root@SERVER:~#

This is with a brand new DDS-3 12/24 GB tape (or an old one for that matter).

I ordered a cleaning tape, but my 'needs cleaning' light doesn't come on.

Help?

Andrew

---

### Post by blueridgedog on 2009-02-10
The ID's look good (7 for the device and 1 for the controller).  You have gone through my book of tricks, but the cleaning tape is the logical next step.

---

### Post by AndyInNYC on 2009-02-10
Well, Staples didn't deliver the cleaning tape - perhaps tomorrow.

I have (finally) found and downloaded all of the bits and pieces required to update the firmware on the DAT drive itself.

What a pain.  This isn't supported by Seagate any longer.  Seagate sold all tape operations to Certance (?) which in turn sold/was absorbed by Quantum.

Buried 90+ pages deep somewhere (and found only through the Dell support forums) were the files I needed.

Now I have to make sure that I can actually use them - I have a Linux loader, hopefully it will be for the right kernel, etc.

If not, I'll need a spare drive on which to install Windows (while hopefully not nuking my array, etc.) just to run the Windows version.

Ah, the joy of a small, mostly for fun, project.


Andrew

---

### Post by handydan918 on 2009-02-10
> If not, I'll need a spare drive on which to install Windows (while hopefully not nuking my array, etc.) just to run the Windows version.


This might be a good spot to consider using virtual box.

---

### Post by egalvan on 2009-02-10
> **blueridgedog said:**
> The ID's look good **(7 for the device and 1 for the controller)**.  You have gone through my book of tricks, but the cleaning tape is the logical next step.

Oops, typo, that... :)

Controller must be 7..
Devices must be anything else..

To the OP, grab a hard drive off that old PowerEdge...
make sure it's ID is set to 3...

when you re-boot the computer, watch for the Adaptec message that allows you to run the set-up for the SCSI card...

the set-up is fairly easy to understand..

you should see three devices....

the adapter card (again, this should show ID of 7)
the tape drive
the hard drive

all on different ID's...

if not, there are deeper issues..

---

### Post by AndyInNYC on 2009-02-10
Egalvan,

I don't understand what you are attempting to tell me (and thanks for trying to tell me something).

Would you break down what you're trying to say in a different way?

I don't have any drives set up from the PowerEdge; these drives were set up on the onboard RAID controller.

It turns out that my firmware on the DAT is 1 revision back from the most up-to-date.  That probably isn't the problem.  Hmm.


Andrew

---

### Post by blueridgedog on 2009-02-10
> **egalvan said:**
> Oops, typo, that... :)

Controller must be 7..
Devices must be anything else..



You are right, I had them reversed, take a look at the guide for the controller:

[http://support.gateway.com/support/manlib/cmponts/control/8502749/02749.htm](http://support.gateway.com/support/manlib/cmponts/control/8502749/02749.htm)

When booting, you should be offered a chance to enter the bios of the controller and set the ID.  If you set it to 7, you can then jumper the drive to be ID 6 or lower and re-test.

---

### Post by egalvan on 2009-02-10
> **blueridgedog said:**
> take a look at the guide for the controller:

[http://support.gateway.com/support/manlib/cmponts/control/8502749/02749.htm](http://support.gateway.com/support/manlib/cmponts/control/8502749/02749.htm)



Hey, nice guide there...

It should help the OP...

ErnestG

---

### Post by egalvan on 2009-02-10
> **AndyInNYC said:**
> Egalvan,

I don't understand what you are attempting to tell me (and thanks for trying to tell me something).

Would you break down what you're trying to say in a different way?

OK, from the tone of your original post, I thought you were up-to-speed on the SCSCI stuff...:(


> I don't have any drives set up from the PowerEdge; these drives were set up on the onboard RAID controller.


And here I thought that you were re-using the parts off that server,
so i suggested borrowing a known-good SCSI hard drive to test with.:(

> 
It turns out that my firmware on the DAT is 1 revision back from the most up-to-date.  That probably isn't the problem.  Hmm.


And on the tape drive, I must claim total ignorance...:lolflag:


Onwards and upwards, me lads....


What i was trying to tell you is that the problem should be broken down into "bite-sized" pieces...

We have several points of failure...

1) computer itself
2) 2940uw card
3) SCSI cable
4) SCSI tape drive

#1 can be ruled out almost entirely, because it runs...
the chance of it not liking the adaptec card is remote...

#2 has to be checked, unless you know for SURE it is working.
booting to the SCSI-Select BIOS is one way of testing.

#3 is similiar. The problem here is that SCSI is a bit more demanding of cable quality... a cheap cable can play hob on the system.

#4 is another possible failure.

Using a SCSI hard drive that was recently working can help reduce the problem points. 
Also, hard drives are easier to test. The Adaptic card has built-in diagnostics for hard-drives,

So my plan was,,,
hook up a hard-drive set to SCSI ID #3
boot the machine and catch the Adaptec "boot screen",
make sure the card is set up to match the info on that nice guide provided by blueridgedog,
run any diagnostics it allows,
run a non-destructive test of the hard drive,
unless it is empty, in which case run a format,

I don't know if this is clear as mud, but it should cover the ground.


ErnestG

---

### Post by AndyInNYC on 2009-02-10
Ah, sorry I was overthinking your reply.

Yes, I have booted into the Adaptec BIOS - this is how I reset the speed down to 5 mb/s.

The cable is from the Dell Server - it is a 3 or 4 position (MB connector and 3 or 4 drives cable).  I'm reasonably certain the cable is undamaged.  I believe I have the DAT on one of the middle connectors.  The DAT drive is terminated using jumpers 11-12.

The original drives (given their age) are probably 15 GB (and HUGE when they were new).  I can drag one up from the basement, but I'm not sure that's neccessary.

If I'm not mistaken, my Adaptec card is ID 6, not 7; I'll look at the BIOS and see if I can reset it.

I just downloaded the Seagate/Certance/Quantum linux program - it found errors and suggested I run a cleaning tape.  If Staples ever delivers, I'll follow that suggestion.

Then I'll brave the basement and pull an old SCSI drive up.  Cue up the spooky music.

Thanks for all of your insight.

Andrew

---

### Post by egalvan on 2009-02-10
> **AndyInNYC said:**
> Ah, sorry I was overthinking your reply.

Yes, I have booted into the Adaptec BIOS - this is how I reset the speed down to 5 mb/s.

The cable is from the Dell Server - it is a 3 or 4 position (MB connector and 3 or 4 drives cable).  I'm reasonably certain the cable is undamaged.  ***_[COLOR="Red"]I believe I have the DAT on one of the middle connectors.  [/COLOR]_***The DAT drive is terminated using jumpers 11-12.

The original drives (given their age) are probably 15 GB (and HUGE when they were new).  I can drag one up from the basement, but I'm not sure that's neccessary.

If I'm not mistaken, **my Adaptec card is ID 6, not 7; I'll look at the BIOS and see if I can reset it.**

I just downloaded the Seagate/Certance/Quantum linux program - it found errors and suggested I run a cleaning tape.  If Staples ever delivers, I'll follow that suggestion.

Then I'll brave the basement and pull an old SCSI drive up. ** Cue up the spooky music.**

Thanks for all of your insight.

Andrew

Whoa there, NEVER leave a SCSI cable dangling! Might as well leave EllieMae at the altar!

The ends of a SCSI cable MUST ALWAYS be connected. If you don't, "Bad Things" can happen... such as data loss.
(a dangling cable end works like mirror, causing massive ringing on the SCSI bus. If it's loose, it's not terminated.)

As to the card being ID 6, again not a Good Thing, but nowhere near as bad as a dangling cable.

(Addams Family Music starts playing.... :popcorn: )

---

### Post by AndyInNYC on 2009-02-10
Well,

I went into the Adaptec BIOS and it seems I had my speed set at 10 MB/s and not 5.  I hadn't turned off the wide negotiations.  Turning that off cut my speed to 5.

I am now running the 3.5 hour diagnostic on the drive.  While I'm sure it still needs cleaning, it is so far (fingers crossed) reading and writing correctly.

We'll have to wait and see what the final result is.


Andrew

---

### Post by AndyInNYC on 2009-02-11
The diagnostic finished this morning - it ran without errors.
The diagnostic is xTalk from Quantum (found somewhere on the website).  It reads, writes, tests, etc.

So the problem was the 10 MB/s rather than 5 MB/s (UW turned off) which was causing the problem.

I'm still not sure why the 5 v 10 makes the difference.  Other posts elsewhere have indicated that it is unneccessary.

But, it seems to be working.

Thanks for everyone's help.

I'll keep you posted if the saga has any new chapters.

Andrew

---

### Post by egalvan on 2009-02-12
> **AndyInNYC said:**
> The diagnostic finished this morning - it ran without errors.

the problem was 10 MB/s rather than 5 MB/s (UW turned off)

not sure why the 5 v 10 makes the difference.  Others have indicated that it is unneccessary.

 it seems to be working.

Thanks for everyone's help.

I'll keep you posted if the saga has any new chapters.

Andrew

Well, refering to the *UW* in 2940*UW*,
the "U" stands for Ultra, as in SPEED, "U" is 40MBs *capable*
the "W" stands for Wide, as in BUS WIDTH, (8bit vs 16bit), W is 16bit *capable*

(then one gets into "open-ended" versus "LVD",
U80, Ultra160, Ultra320, Ultra320 LVD, etc...) :)

As to why your tape drive works at 5 and not at 10 or above;
the tape drive may only run at 5mb,
the jumpers on the drive may be set for 5mb (if this is an option)
the SCSI card may be locked at 10mb
the cable may not be Fast (or higher) rated (Fast=10mb)
if it is still not on the end connector, Termination may be mangled.
termination may not be mangled.  :)


Do I miss SCSCI?

Actually, yes. It was (and still is) capable of giving very high throughput rates, do to multiple channels available, the head seek logic, and the fast spindle speeds.
Admittidly, modern SATA drives are getting the seek logic, and they are getting faster.
But 10k SCSI´s are standard, and 15k are widely available.

---

