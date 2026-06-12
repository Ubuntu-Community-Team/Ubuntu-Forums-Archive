---
title: "logitech quickcam connect (e2500)"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by icanimagine on 2009-12-17
n00bette here, looking for advise. so i've been trying real hard all day to get my old *** webcam to work with my old *** computer and my brand spankin' new installation of karmic koala. i found a couple of threads in the forums relating to this and after getting lots of disappointing messages in my terminal following dusty tutorials, i have decided to swallow my pride and ask the community my damn self. so here it goes:

 i have a logitech quickcam connect (e2500) and i have recently installed ubuntu 9.10 as my sole os with a very meagre background using linux at all. how the hoo-haw do i get these to work together in plainish english?

numbers in case they matter:
m/n v-ucv39
p/n 860-000114
pid lz829bb

 i'm pretty good with copying and pasting things into the terminal, and i vaguely know what the synaptic package manager is and how to work the phabulous software center, but when i look at some of these threads where you pros try to explain things to things to the new kids, i have issues trying to wrap my mind about what you want them to do. 

beware: if you answer i might keep asking questions. i have a few other outdated peripherals i'd love to see up and working with my setup!

peace out! 

\\:D/

---

### Post by patrickballeux on 2009-12-17
It seems that the driver to use that webcam is gspca_zc3xx.

Can you validate that this module is loaded?

> lsmod | grep gspca_zc3xx

If it is not, then run this command:

> sudo modprobe gspca_zc3xx

then

> dmesg

This will give you some details about what happenned...

When you say it is not working, what software have you tried?  One quick test to validate that the webcam is working would be installing Cheese from the repos.

Let me know!

---

### Post by icanimagine on 2009-12-17
okay, pardon my ignorance. by "validate this module is loaded" you mean copy and paste that into the terminal and try to decipher what the response means? um it says:
> 
[imagine@hugo:~$ lsmod | grep gspca_zc3xx 
gspca_zc3xx            47580  0 
gspca_main             22812  1 gspca_zc3xx
imagine@hugo:~$ 
hmm....then i do the other stuff and it says:

> Temperature above threshold, cpu clock throttled quite a bit, which worries me. don't know if it has to do with why the cam is not working.

i was testing it in camorama and luciole. when i just tried cheese, it looks like it worked for maybe a few milliseconds and then went to black with a little green line on the bottom. grrrrr....... ](*,)

---

### Post by icanimagine on 2009-12-17
oh...i ran that dmsg thingy again and noticed it said something about the usb so maybe it's relevent. then again, my internet works with a usb wifi adapter thingy so it could be talking about that. don't know. mongo only pawn in game of life. anyway, here's the *** end of meh ominous messages:

> [14519.689299] CPU0: Temperature/speed normal
[14519.775712] CPU0: Temperature above threshold, cpu clock throttled (total events = 11507)
[14519.776820] CPU0: Temperature/speed normal
[15124.334643] usb 2-1: USB disconnect, address 2
[15124.334916] gspca: disconnect complete
[17454.164193] usb 2-1: new full speed USB device using ohci_hcd and address 3
[17454.367920] usb 2-1: configuration #1 chosen from 1 choice
[17454.370849] gspca: probing 046d:089d
[17454.370859] zc3xx: Sensor MC501CB
[17454.382873] gspca: probe ok
[17454.383017] gspca: probing 046d:089d
don't know what all that means, but the probing sounds ok.

peace out

---

### Post by patrickballeux on 2009-12-20
> **icanimagine said:**
> oh...i ran that dmsg thingy again and noticed it said something about the usb so maybe it's relevent. then again, my internet works with a usb wifi adapter thingy so it could be talking about that. don't know. mongo only pawn in game of life. anyway, here's the *** end of meh ominous messages:

don't know what all that means, but the probing sounds ok.

peace out

Good!  Seems like your webcam is recognized and loaded.  So now, have a look in "/dev" to see if you have any video devices.

in a console, type : ls -l /dev/video*

You should have at least /dev/video0

This device should be part of the "video" group.  Make sure that your user is part of that group.  If I remember well, in the permission of your users, you have something regarding webcams/video devices that should be checked to give you access

If it is not, check it, log out and log in...

Then, try to use Ekiga or Cheese (from the repositories) to validate if your webcam is working.

Or install WebcamStudio, it will give you more details about your video devices (In the about menu).

Let me know!

Patrick

---

### Post by jlg317 on 2009-12-28
My name is Jose, I have somewhat of a similar problem, my webcam only starts working if I use amsn, other than that it wont work, any idea why that happens and how I can attempt to fix it???:)

---

### Post by xbaez on 2010-01-03
When I connect my camera, I see this in /var/log/messages:

Jan  2 23:43:01 xavier-desktop kernel: [14708.751147] usb 2-2.1: new full speed USB device using ehci_hcd and address 12
Jan  2 23:43:01 xavier-desktop kernel: [14708.863357] usb 2-2.1: configuration #1 chosen from 1 choice
Jan  2 23:43:01 xavier-desktop kernel: [14708.863802] gspca: probing 046d:089d
Jan  2 23:43:01 xavier-desktop kernel: [14708.863806] zc3xx: Sensor MC501CB
Jan  2 23:43:01 xavier-desktop kernel: [14708.864282] gspca: probe ok
Jan  2 23:43:01 xavier-desktop kernel: [14708.864326] gspca: probing 046d:089d
Jan  2 23:43:04 xavier-desktop kernel: [14712.351122] gspca: usb_submit_urb [0] err -28

So there is an error 28

anyway, Ekiga shows the camera
CameraMonitor tells me when the camera is connected or not
Skype works with the Camera microphone
and in Skype I can select /dev/video0

guvcview also works
Cheese also works

My question is

what do I have to do to make this camera work in Skype?

my username blabla was not part of the group video

I'm restarting the X session

I will really appreciate if can get help here since this is the only thing that doesn't works in Ubuntu

---

### Post by Methuselah on 2010-01-03
After you're a member of the video group and have logged back in check the settings in skype.

Hit the little skype logo at the bottom of the window and select options.
Choose video devices on the left.
Make sure 'Enable Skype Video' is checked.
Under 'Select Webcam' make sure your gspca webcam is selected then click test in the little area to the right.

---

### Post by xbaez on 2010-01-06
> **Methuselah said:**
> After you're a member of the video group and have logged back in check the settings in skype.

Hit the little skype logo at the bottom of the window and select options.
Choose video devices on the left.
Make sure 'Enable Skype Video' is checked.
Under 'Select Webcam' make sure your gspca webcam is selected then click test in the little area to the right.

It doesn't works

any other suggestion?

---

### Post by Methuselah on 2010-01-06
This is honestly starting to look like an issue with skype.
If it works with other programs skype should work.
You might want to ask about this on the skype forums for linux.

[http://forum.skype.com/index.php?showforum=18](http://forum.skype.com/index.php?showforum=18)

---

### Post by xbaez on 2010-01-06
> **Methuselah said:**
> This is honestly starting to look like an issue with skype.
If it works with other programs skype should work.
You might want to ask about this on the skype forums for linux.

[http://forum.skype.com/index.php?showforum=18](http://forum.skype.com/index.php?showforum=18)

Ok, I started a thread on Skype:

[http://forum.skype.com/index.php?showtopic=507901](http://forum.skype.com/index.php?showtopic=507901)

---

