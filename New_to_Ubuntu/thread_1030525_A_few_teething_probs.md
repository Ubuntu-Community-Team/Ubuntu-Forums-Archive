---
title: "A few teething probs"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by pseudonym_anon on 2009-01-04
I have the latest Ubuntu installed in a Virtual Machine, here are my list of problems, help with any would be gratefully recieved:
[LIST=1]
[*]I dont have any sound
[*]When I try to set visual effects, I get an error stating that they cannot be set. I am using a very new PC, so I am assuming that maybe it does not recognise the capability of my graphics card. Is there any way to test this?
[*]When I start Ubuntu in the Virtual Machine it states the display in the guest OS is set to 16bit, and it would like it to be set to 32 bit. Is "Guest OS refering to Ubuntu or the OS the VM is running in?
:confused:[/LIST]

---

### Post by jimmy the saint on 2009-01-04
1)sound - did you activate a sound card in the mangement section of the VM software you are using.  A lot of VM software setups don't automatically set up a virtual sound card.
2)Effects:  You cannot virtualize a 3d acceleration capable video card.   The guest (Ubunutu) is not using your video card.  It is using a fake card that is being simulated by the virtual machine.  It is the equivilant of a crappy onboard video card from approx 1998
3)The guest OS is the one installed on your virtual machine.
  The host OS is the one installed on your "real" machine.

---

### Post by pseudonym_anon on 2009-01-04
I have activated sound in the VM but I now get a x next to the speaker in Ubuntu and the error:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

---

