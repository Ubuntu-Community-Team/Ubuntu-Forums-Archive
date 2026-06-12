---
title: "Experiencing slow boot. Whats wrong?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by madsc89 on 2009-10-30
I've been using Karmic since beta, and originally I thought it was good, but as updates where installed, boot grew slower and slower. It is installed on a ext4 partition on an Intel x25-m 80 GB, so it should boot in 5 seconds or so? I've attached a video of the boot sequence from grub. As you can see, it takes real long before the splash appears, and during that time, the led for CPU activity is not blinking... Also some text flashes, and I am asked to log in (which also dissapear). What is wrong, or how do I find out whats wrong? The system is now a fresh install from RC fully updated.

Thank you.

---

### Post by madsc89 on 2009-11-02
No one?
This is really dissapointing... It was a lot faster during beta...
I believe this slow boot is related to some uppgrades/program installations, but I can't possibly know which one..

Attached is a boot Chart if that can be of any help..

---

### Post by Pebble2009 on 2009-11-09
Hallo.
My boot up time was at 1 min 32 secs before i tried this.
Now its 49 seconds

Hope this helps you.:D

):P

 [http://www.omgubuntu.co.uk/2009/10/get-dramatically-faster-boot-times-in.html](http://www.omgubuntu.co.uk/2009/10/get-dramatically-faster-boot-times-in.html)

---

### Post by madsc89 on 2009-11-09
Thank you.
However, this is a tweak to get a healty system even faster. In my system there is something wrong, causing it to be slower than normal. I want to fix this problem.

---

### Post by NFblaze on 2009-11-09
I dont know either, I'm just marking this incase anyone has an idea. My boot times where much faster also in the Alphas, Beta, and RC until I did an upgrade to the Final. Probrably up about 5-8 seconds.

---

### Post by Psychoscorpic on 2009-11-10
Yep - me too. Karmic upgrade from Jaunty is booting approximately twice as long as Jaunty needed: Now averages 1min 54 seconds.
I was expecting 30 seconds or so. Bummer.

Boot process also a bit weird:
After GRUB, it goes to two lines of text saying it is starting up.
Then black & white Ubuntu logo for about 35 seconds.
Then black screen for another 1/2 minute (screen flashes a few shades of black - like differing power states to the LCD)
Jumps back to the two lines of text saying it is starting up, for about 5 seconds.
Then the new boot animation for about 25 seconds.
X-Cursor overlays onto this, and system sounds play (startup ditty followed by Skype logon). 
Switches to blank desktop and an empty top bar (I have killed the bottom bar in favour of Cairo Dock)
A few seconds later the top bar icons populate and the desktop appears correctly.

Another post I've seen describes this as a "double-boot" and judging by the time used, and the reverting to the two lines of text, it would almost appear so. (I suspect it's more a matter of display systems fighting for dominance.)

Only other hassle I had is NoScript add-on in Firefox has a display problem: The info boxes are black (text seems to be rendering behind the background). Oddly this is only on the main panel - the fly-out panels render correctly.

Pity - the rest of my Karmic experience has been good so far (better WiFi signal strength is a real bonus)

Anyone with any solutions to the above?

> **madsc89 said:**
> No one?
This is really dissapointing... It was a lot faster during beta...
I believe this slow boot is related to some uppgrades/program installations, but I can't possibly know which one..

Attached is a boot Chart if that can be of any help..

---

### Post by madsc89 on 2009-11-10
This is really starting to frustrate me.
I finally did a complete fresh new install. I firmatted the partition, and installed fresh from a newly downloaded ubuntu 9.10 64-bit. The boot is still as slow, with all the same flashing text and annoying dead time. I've attached a couple of boot charts (In a zip folder because of the forums max height policy on pictures). This is from a completely fresh install. The only thing I've done on it is install the bootchart package and open FF for ubuntuforums.
There is something seriously wrong here! The video in first entry is still valid. As I earlier said, Karmic was a lot faster during first time of beta. Also remember this is on a Intel x23-M SSD, so it should be a lot faster. Make a note on the long time in the boot charts where nothing is happening!

Any help will be appreciated. Otherwise, I am forced to abandon Karmic.

---

### Post by QIII on 2009-11-10
This is a known issue, and it is a frustrating kick in the groin considering the fact that we all anticipated much faster boot times.

While I am quite sure that the developers are aware of this and are working the issue, I think that we may all have to bear with this for the time being.  I would say to beware of third-party "tweaks" until this is resolved.

I have a quad-core machine with 8GB of memory, and I still get slow boot times.  40 - 60 seconds some times.

(I must say, however, that I don't quite have enough time to pour a cup of coffee while I wait ... like I do with other OSs...)

---

### Post by SjoerdC on 2009-11-10
same here; where is the solution?!

---

### Post by madsc89 on 2009-11-10
> **QIII said:**
> This is a known issue, and it is a frustrating kick in the groin considering the fact that we all anticipated much faster boot times.

While I am quite sure that the developers are aware of this and are working the issue, I think that we may all have to bear with this for the time being.  I would say to beware of third-party "tweaks" until this is resolved.

I have a quad-core machine with 8GB of memory, and I still get slow boot times.  40 - 60 seconds some times.

(I must say, however, that I don't quite have enough time to pour a cup of coffee while I wait ... like I do with other OSs...)

Thank you for the reply. It is good to know it is being delt with. Where do I keep a look out for news on the problem being fixed? I decided to try Mandriva while this problem persists, so I wont notice any change on my system.. Could you perhaps poste here when it is solved? Or is there a bug report I can follow or something like that?

---

### Post by cjbarrow on 2009-11-10
I have been using 9.10 64bit since Alpha 2 and the boot speed was excellent, I decided to do a fresh install of the 32bit version the other day and 60% of the time it takes nearly 2 minutes to boot.

Hope they fix this soon or I will go back to 64bit version.

Chris.

---

### Post by madsc89 on 2009-11-11
I appreciate it if you keep us updated about your problem! Do your boot sequence look anything like mine (see atachement in first post)?

---

### Post by qwety on 2009-11-11
[https://bugs.launchpad.net/ubuntu/karmic/+source/sreadahead/+bug/432089](https://bugs.launchpad.net/ubuntu/karmic/+source/sreadahead/+bug/432089)

---

### Post by madsc89 on 2009-11-11
Are you sure this is the same bug? I am running on a very fast SSD...
Also it seems there are multiple factors on my system. (See the video on first post). One thing I am really curious about is the "tty1" -login.

---

### Post by coronacolada on 2009-11-11
Yeah, I used to boot in 27 seconds. Now I've got 1:47. 

Bah.

---

### Post by zarf on 2009-11-12
No solution here but i will be watching the thread with interest. I am running an older machine here but several minutes to load up?
I get to "GRUB LOADING" and wait 1:45, then once I get to the option screen and hit enter its another 45 seconds until the screen goes blank and then it is 3-4 minutes until I get the sign in page.

Ha, to think I came back to this because XP was slow.

---

### Post by madsc89 on 2009-11-12
Is this a known bug? Perhaps several? Can those of you who experience slow boot describe you boot sequence? What text flashes? Are there any pictures? Does the screen flimer?

My sequence:
- Select Ubuntu in Grub
- 5-10 seconds of a _ flashing in top left corner, rest of screen black.
- less than one second flash of a scewed picture of the grub menu.
- ~5 seconds of a white glowing ubuntu logo.
- less than one second flash of text. Filling top half of the screen.
- one second with something like ".... tty1 ***** login:"
- then something gets printed on that line.
- some different shades of black flash on the screen
- mouse appears
- ubuntu splash
- desktop

The computers led for CPU activity is only blinking during ubuntu splash and white ubuntu logo...

---

### Post by madsc89 on 2009-11-13
I decided to try Linux Mint 8 (based on Karmic) to see if the problem persisted.

It mostly does. My boot is a little better now, but there is still some time used at nothing at all... The very annoying tty1 bit is not present now.

This is a 32 -bit version.

I will attach a bootchart if I get to it...

---

### Post by ukripper on 2009-11-13
can you attach "dmesg-log-file" after running below command:

```
dmesg > dmesg-log-file
```

---

### Post by madsc89 on 2009-11-13
Of course I can.

Attached as a zip archive...

---

### Post by ukripper on 2009-11-13
Found few interesting error messages regarding your cdrom. Can you disable cdrom in bios and try to reboot and see if that makes any difference.
> [  157.342626] cdrom: This disc doesn't have any tracks I recognize!
[  157.411171] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.411181] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.411192] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  157.411205] end_request: I/O error, dev sr0, sector 0
[  157.411214] Buffer I/O error on device sr0, logical block 0
[  157.411226] Buffer I/O error on device sr0, logical block 1
[  157.411233] Buffer I/O error on device sr0, logical block 2
[  157.411239] Buffer I/O error on device sr0, logical block 3
[  157.411246] Buffer I/O error on device sr0, logical block 4
[  157.411253] Buffer I/O error on device sr0, logical block 5
[  157.411260] Buffer I/O error on device sr0, logical block 6
[  157.411267] Buffer I/O error on device sr0, logical block 7
[  157.411273] Buffer I/O error on device sr0, logical block 8
[  157.411280] Buffer I/O error on device sr0, logical block 9
[  157.418959] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.418968] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.418978] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  157.418990] end_request: I/O error, dev sr0, sector 0
[  157.422256] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.422266] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.422276] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  157.422288] end_request: I/O error, dev sr0, sector 0
[  157.468467] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.468478] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.468488] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  157.468500] end_request: I/O error, dev sr0, sector 0
[  157.472777] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.472789] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.472800] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  157.472813] end_request: I/O error, dev sr0, sector 0
[  157.509482] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.509493] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.509503] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  157.509515] end_request: I/O error, dev sr0, sector 0
[  157.512759] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.512771] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.512783] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  157.512796] end_request: I/O error, dev sr0, sector 0
[  160.695503] warning: `growisofs' uses 32-bit capabilities (legacy support in use)

---

### Post by madsc89 on 2009-11-13
I didn't notice any difference now. My bios doesn't giva an option to disable the DVD, so I removed it from the computer. BIOS correctly reported the slot to be empty. Still the same result, however.

I'll attach a new log file along with a boot chart in a new zip folder.

In the attachment is both the log, a new bootchart (from this boot) and an old bootchart (from yesterday, with almost clean install).

Thank you very much!

---

