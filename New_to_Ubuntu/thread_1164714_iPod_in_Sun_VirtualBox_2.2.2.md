---
title: "iPod in Sun VirtualBox 2.2.2"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by psychx on 2009-05-19
I have set up Windows XP Home (SP2) in Sun's VirtualBox (not the OSE) v2.2.2

I have everything running fine, and Windows XP notices USB just fine. My problem is actually setting it up to recognize the iPod. My Ubuntu 8.10 notices the iPod just fine, as well. (ubuntu host, windows guest)

I know there is most likely a filter that I have to configure in the VirtualBox USB menu. I am just not sure what the device ID's are or anything. Would someone be able to help me out?

Oh, and by the way, this is a 16GB iPod Nano

I have found everything I need setting all of this up, except for actually getting the iPod recognized. Thank you for any support.

---

### Post by psychx on 2009-05-20
Has anyone had any experience with this? Maybe I'm at the wrong site or forum.. Like I said, everything else is set up, I think I just need the information for the usb filter in VirtualBox.

---

### Post by lilmagnus on 2009-05-20
Make sure your iPod is plugged in. Go into settings of your XP VM, hilight USB, then click on the Add Filter button (or Alt-Ins). See the screenshot. The iPod should be listed there. Hope this works for you. Keep in mind that the filters will provide EXCLUSIVE access to the USB device. You will not be able to use it with Ubunutu when you have the VM running. I found that out by mistakenly adding a filter for my USB hard drive.:redface:

---

