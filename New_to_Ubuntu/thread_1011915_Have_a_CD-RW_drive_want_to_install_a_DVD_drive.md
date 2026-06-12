---
title: "Have a CD-RW drive want to install a DVD drive"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by luomat on 2008-12-15
I just installed 8.10 on a Dell Dimension 4600 (aka "fairly generic Dell tower).

The Dell only has a CD-RW drive installed, and I've like to install a DVD drive so I can watch movies in VLC and/or convert DVDs with HandBrake.

This is my first experience using Ubuntu, so I'm not sure how to go about installing new hardware.  Is it as simple (ideally) as simply shutting down the computer, removing the CD-RW drive and installing the DVD drive?

I have a Pioneer DVD-RW drive in an external case at home that I plan to use. I could remove it from that case and use it internally in the Dell, or leave it in the case and use it externally.

Obviously it's a little neater if I can put it internal (one less thing cluttering up my desk).

Would it be better/easier from Ubuntu's side of things to attach that externally via USB or remove the original internal CD drive and replace it with the DVD drive?

Do I have to do anything to tell Ubuntu that I have installed new hardware or will it check on startup?

Thanks!

TjL
(finding it very strange to be such a novice)

---

### Post by Michael.Godawski on 2008-12-15
> Would it be better/easier from Ubuntu's side of things to attach that externally via USB or remove the original internal CD drive and replace it with the DVD drive?

Do I have to do anything to tell Ubuntu that I have installed new hardware or will it check on startup

I would just put in the dvd- rom and remove the cd-rom. Let Ubuntu recognize the new hardware. Usually it is done without any manuall tweaking.

---

### Post by luomat on 2008-12-15
Thanks! I will try that tomorrow!

---

### Post by DGortze380 on 2008-12-15
Given the age of the machine, I assume it's an IDE Drive.

Get your new drive. You can use the external by taking it out of the case depending on what type of connection it has. I can't tell you this, you'd have to open it.

Check you new drive. There should be a jumper on the back. If this is going to be the only drive in the machine, set the jumper to Master. If it is the second drive in the machine, be sure one drive is set to Master and one drive is set to Slave.

Open your case.

Your current CD-RW (if it's the only drive in the case) should be connected to the Master connector on the ribbon cable. If your new drive is going to be the only one in the case, remove this ribbon cable (careful, they take some force and tend to tear), remove the old drive, replace it with the new drive, reattach the ribbon cable.

If this is the second drive in the case, Add the new drive below your current drive, and attach the available slave IDE connector.

---

### Post by laidback on 2008-12-15
In my experience as long as the POST (Power On System Test) detects the harware then Ubuntu can configure it. POST happens when you switch the power on and before Ubuntu is loaded. My screen displays the hardware detected in a list, but you have to be quick to read it as the system rushes off to boot Ubuntu almost immediately. There's usually a button to press to get into the BIOS/CMOS so you can view things in a more leisurely manner. 

Check the jumper settings on the back of any hdd/dvd-rom, I have found that Linux doesn't like the Cable Select option. So I set mine to Master or Secondary. The unit itself should have a description of the jumper settings printed on it.

---

### Post by Hospadar on 2008-12-15
A brief note on watching dvds:

Typical movie dvds are encrypted (The video files that is) with an encryption scheme called css.  For legal reasons, stock ubuntu doesn't come with the ability to decrypt dvd video.  You'll need to get libdvdcss from the medibuntu repositories.  They have a very nice guide on how to get their stuff installed.
Go here:
[http://www.medibuntu.org/](http://www.medibuntu.org/)

follow the guide at "repository howto" to get their repositories working, then search in synaptic (System->Administration->Synaptic) for libdvdcss2 and install.  You'll now be able to watch dvds.

if you search in synaptic for "medibuntu" you'll find all the other packages they offer.  They have some convenient packages to install google earth, adobe acrobat, windows and other codecs, among other things.

Largely they offer support for media formats that aren't supported by regular ubuntu.

---

### Post by luomat on 2008-12-15
> **DGortze380 said:**
> Given the age of the machine, I assume it's an IDE Drive.

Yes, I put a new hard drive in it when I installed Ubuntu and it's definitely IDE.

> **DGortze380 said:**
> Get your new drive. You can use the external by taking it out of the case depending on what type of connection it has. I can't tell you this, you'd have to open it.

"DVD in External Case" is also IDE. Should have mentioned that.


> **DGortze380 said:**
> Check you new drive. There should be a jumper on the back. If this is going to be the only drive in the machine, set the jumper to Master. If it is the second drive in the machine, be sure one drive is set to Master and one drive is set to Slave.

Ugh, I was never good at this stuff.

The hard drive and CD/DVD drive are on different "Master/Slave" chains right?  So when you say "Only Drive" you mean on that ribbon (obviously there's a hard drive in there too, but that's usually on a second ribbon?)


Open your case.

> **DGortze380 said:**
>  Your current CD-RW (if it's the only drive in the case) should be connected to the Master connector on the ribbon cable. If your new drive is going to be the only one in the case, remove this ribbon cable (careful, they take some force and tend to tear), remove the old drive, replace it with the new drive, reattach the ribbon cable.

If this is the second drive in the case, Add the new drive below your current drive, and attach the available slave IDE connector.

I don't see any reason to have a CD-RW and a separate DVD-RW in there, so I'll probably just take out the CD-RW.

Thanks for the heads up about the master/slave stuff.

TjL

---

### Post by laidback on 2008-12-16
Master/Slave (secondary) ..yes it's per ribbon cable.

---

### Post by grungedoobie on 2008-12-29
I did the exact same thing today with a Pioneer External USB DVD/RW drive.  A computer had two drives that were incompatible with each other.  One a CD/RW and the other a DVD/R.  Both drives refused to work unless they were the master. (Swapping IDE cables becomes a real pain after a while.  8-P)

The computer I put it on is a dual boot system running Windows XP and Kubuntu 8.04.

When I pulled the USB external case apart, it sure enough had a USB/IDE interface, and when the hardware was connected to the desktop neither OS had any problem with the drive.


Cool Beans 8-)

---

