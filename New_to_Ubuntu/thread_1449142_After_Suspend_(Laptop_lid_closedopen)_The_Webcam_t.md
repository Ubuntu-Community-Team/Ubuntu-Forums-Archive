---
title: "After Suspend (Laptop lid closed/open) The Webcam turns on"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by tmx84 on 2010-04-07
Can anyone help me with this issue.  Every time the laptop suspends, weather it's by key or by closing the lid.  When i take it out of suspend, the built in webcam is always on.  I'm fairly new to Ubuntu so usually i just run guvcview, than close it and it will turn the webcam off. 

Sorry if there is a fix already posted somewhere but i couldn't find it!

---

### Post by mörgæs on 2010-04-07
I don't know of a sure fix, but an easy test is trying Ubuntu 10.04 and see if it works better:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It is still in beta, but only a few weeks from being an official release. It has behaved well on all machines where I have tried it.

---

### Post by tmx84 on 2010-04-07
Mmm, I could try that as well, but i think i may have fixed it.  Which is actually kind of odd, cause i went into /usr/lib/pm-utils/sleep.d/ and edited 99video and commented out resume_fbcon, which stopped the webcam from turning on.  

```
resume_fbcon()
{
	local con
	for con in /sys/class/graphics/*/state; do
		[ -f $con ] || continueubuntu usb2.0 uvc vga webcam
		echo 0 >"${con}"
	done
}
```

but i commented it out here...

```
resume_video()
{
	# We might need to do one or many of these quirks
	quirk "${QUIRK_PCI_SAVE}" && 		pci_restore
	quirk "${QUIRK_VBE_POST}" && 		vbe_post
	quirk "${QUIRK_VBESTATE_RESTORE}" && 	vbe_restorestate
	quirk "${QUIRK_VBEMODE_RESTORE}" && 	vbe_restoremode
#	resume_fbcon 	# also should be handled by a quirk.
	quirk "${QUIRK_RADEON_OFF}" && 		radeon_on
	quirk "${QUIRK_DPMS_ON}" && 		vbe dpms on
	quirk "${QUIRK_RESET_BRIGHTNESS}" && 	reset_brightness
	return 0  # avoid spurious hook exit failure message.
}
```

But the odd part was, i went back in and changed it back to original, and the webcam is still no longer turning on.  So i'm a bit confused?  But everything seems to be working alright.. so oh well!

---

