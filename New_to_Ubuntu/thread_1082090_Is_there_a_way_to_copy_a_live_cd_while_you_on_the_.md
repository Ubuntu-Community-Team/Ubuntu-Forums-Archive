---
title: "Is there a way to copy a live cd while you on the live cd."
date: 2009-02-27
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-02-27
heres the log I got when I tried to copy the live cd onto another dvd and got permission errors.

Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
BraseroReadom called brasero_job_get_action
BraseroReadom getting varg
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_set_output_size_for_current_track
BraseroReadom got varg:
BraseroReadom stopping
BraseroReadom called brasero_job_get_action
BraseroReadom output set (IMAGE) image = /tmp/brasero_tmp_PFEPPU toc = (null)
BraseroReadom called brasero_job_get_session_output_size
BraseroReadom getting varg
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_fd_out
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroReadom reading last track from sector 0 to 516048
BraseroReadom called brasero_job_get_image_output
BraseroReadom got varg:
	readom
	dev=/dev/scd1
	-nocorr
	-noerror
	-sectors=0-516048
	-f=/tmp/brasero_tmp_PFEPPU
BraseroReadom launching command
BraseroReadom stderr: Error trying to open /dev/scd1 exclusively (Device or resource busy)... retrying in 1 second.
BraseroReadom stderr: Error trying to open /dev/scd1 exclusively (Device or resource busy)... retrying in 1 second.
BraseroReadom stderr: Error trying to open /dev/scd1 exclusively (Device or resource busy)... retrying in 1 second.
BraseroReadom stderr: Error trying to open /dev/scd1 exclusively (Device or resource busy)... retrying in 1 second.
BraseroReadom stderr: Error trying to open /dev/scd1 exclusively (Device or resource busy)... giving up.
BraseroReadom called brasero_job_error
BraseroReadom finished with an error
BraseroReadom asked to stop because of an error
	error		= 10
	message	= "you don't seem to have the required permissions to access the drive"
BraseroReadom stopping
BraseroReadom got killed
Session error : you don't seem to have the required permissions to access the drive (brasero_burn_record burn.c:2270)

---

### Post by LowSky on 2009-02-27
Well ... personally I have never even tried to to burn a LiveCD while running the LiveCd but I could see it being an issue, as the LiveCd cant leave the Tray, maybe if you have two drives you could try it, but you cant use copy and you really cant download a new ISO unless you have alot of RAM.

you have to remember that the LiveCd runs from your RAM and doesnt use your hard drive at all, also when you click to launch any application you will need to load it from the LiceCD

---

### Post by Ben Page on 2009-02-27
try to log in as root, or do a sudo bash...In LiveCD you are logged in as a user with limited permissions so in order to write some system files you need a root access. Also, you are trying to write files that are already in use so it is nearly impossible to do this. Someone maybe does know how to do it...

---

### Post by sydbat on 2009-02-27
I don't think it's possible because, as stated before, the Live CD itself is in use.

However, if you have 2 CD drives (with at least 1 that can burn a CD) and have the .iso on the hard drive of the computer you are running the Live CD on, you should be able to burn that .iso...but it may be a realllllly slow burning process (because everything is going through your RAM).

---

### Post by llamabr on 2009-02-27
Yes, the permissions errors are not your concern.  Just run as sudo.

The issue will be enough memory to run everything you want.  How much ram do you have?

Why are you trying to do this?  Do you not have another system that can burn a cd?

---

### Post by pastalavista on 2009-02-27
I believe you could install it to a USB thumb drive if you install [UNetbootin]("http://sourceforge.net/projects/unetbootin"). It runs much faster than a live CD but only on newer machines capable of booting from USB.

---

### Post by egalvan on 2009-02-27
Puppy Linux is a distro that runs completely in RAM,
allowing you to eject the cd.

PartedMagic is another.

I know Puppy has a CD burner app, I don't remember if PartedMagic does.

There are others out there (Knoppoix?)

Depending on how much RAM you have, this can take considerable disc swapping.

---

### Post by Pbethe on 2009-02-27
> **egalvan said:**
> Puppy Linux is a distro that runs completely in RAM,
allowing you to eject the cd.

PartedMagic is another.

I know Puppy has a CD burner app, I don't remember if PartedMagic does.

There are others out there (Knoppix?)

Depending on how much RAM you have, this can take considerable disc swapping.

Knoppix is pretty light-weight.  If you have 1000M of RAM you can use the boot command "knoppix toram" and free up the drive you are booting from once the CD is loaded into RAM.

---

### Post by theozzlives on 2009-02-27
This has gotta be the strangest Thread I've seen so far. Does your computer have an operating system and burning software? Just download the ISO and burn a copy, or copy it booting from your HD.

---

### Post by ericeclifford on 2009-02-27
I have 2 gigs of ddr2 533 mhz ram and I was also wondering can i copy the live cd ( While Running) to a usb stick or any external hard drive than can hold it. My OS is ubuntu 8.04.2 and its the live cd that I am running on(non installed on HD) and i am trying to copy the live cd while running to a blank cd for a back up.

---

### Post by ericeclifford on 2009-02-27
BTW I know I can do it on a harddrive but I want to give a live cd to my mom and have her just use it for internet but I want her to be able to make a back up if needed by herself.

---

### Post by WIndows to LInux on 2009-02-27
optical drives (DVD/CD) only have one lens to read CDs with, so if it can be done, it would take a very long time
Let Knoppix 5.11 (the most up to date that can be still be loaded into RAM)
do the disk copying/backup

---

### Post by ericeclifford on 2009-02-27
Can u do it for ubuntu?

---

### Post by Pbethe on 2009-03-01
> **ericeclifford said:**
> Can u do it for ubuntu?
Visit [www.knopper.net](www.knopper.net) and read up on it.  Knoppix is designed to boot from a cd and not be installed to a hard drive.  Klaus Knopper just released a beta version 6.  I have not had a lot of success with it, but you should still be able to get the 5.1.1 cd.

---

### Post by pastalavista on 2009-03-02
Your mom's internet experience (and everything else) would be very slow if she only uses a live CD. Why don't you just install it on her PC... in a dual boot to make sure she likes it. You can install it with Wubi right inside of windows or it's own partition and easily uninstall it later if need be. A live CD experience can be pretty frustrating, but she'll be amazed by a full install.

---

