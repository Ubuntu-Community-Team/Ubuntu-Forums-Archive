---
title: "no usb option for printer Hardy 8.04?"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by iansane on 2009-09-17
Hi,

Can anyone tell me why there is no option for usb printer when I try to add a printer?

I used to have my cannon mp150 installed and working just fine but now when I try to add a different usb printer it asks for the uri but there's no option for a usb.

I don't know what a uri is so I tried manually typing in USB:// but that didn't work.

Why is stuff disapearing from cups? I noticed a while back that I had to go and install cups-pdf which used to be already installed by default.

Isn't the goal to improve and add functionality? Not to take away from it?

Also can anyone recomend a standard hp ink jet color printer that's inexpensive and works with ubuntu?

The guys in the store say everything works with linux but when I mention ubuntu they say ubu-what? lol they don't have a clue about linux so they are no help in finding a good printer.

---

### Post by cmnorton on 2009-09-17
Have you used [http://localhost:631?](http://localhost:631?) You'd need to be in lpadmin's group to use the Administrative functions. This sounds like your printer would be a locally attached printer, not so much USB printer. If I had one here, I'd try it out for you. I've got Kubuntu 8.04. 

Ubuntu's print interface is very good, and much better than Red Hat's, but I still like the CUPS interface better.

---

### Post by philinux on 2009-09-17
> **iansane said:**
> Hi,

Can anyone tell me why there is no option for usb printer when I try to add a printer?

I used to have my cannon mp150 installed and working just fine but now when I try to add a different usb printer it asks for the uri but there's no option for a usb.

I don't know what a uri is so I tried manually typing in USB:// but that didn't work.

Why is stuff disapearing from cups? I noticed a while back that I had to go and install cups-pdf which used to be already installed by default.

Isn't the goal to improve and add functionality? Not to take away from it?

Also can anyone recomend a standard hp ink jet color printer that's inexpensive and works with ubuntu?

The guys in the store say everything works with linux but when I mention ubuntu they say ubu-what? lol they don't have a clue about linux so they are no help in finding a good printer.


Just plug the one usb printer you are trying to set up. What's the make and model.

---

### Post by iansane on 2009-09-17
Thanks cmnorton,

I don't understand what you mean by "not so much usb"

It is plugged in with a usb cable to a usb port.

I tried installing hplip and when it looks for the printer it says no device found so I think it's a usb problem.

Wouldn't that uri for localhost:631 be for a network attached printer?

---

### Post by iansane on 2009-09-17
OK I figured it out.

I wasn't paying attention to the power light. It appears to be on when it's plugged in but at some point the power got turned off yet the power light stays on. I hit the power button again and ran lsusb and there it was.

Once detected in lsusb it was just a matter of running the hp device manager. Big props to HP for the HPLIP installer. I had to install the newer version from HP because the one in Hardy didn't support my printer but it works now.

Thanks

---

### Post by iansane on 2009-09-17
> **philinux said:**
> Just plug the one usb printer you are trying to set up. What's the make and model.

Thanks philinux. I only have one printer. It was a ID10T error on my part.

Oh and it is a HP F4480. If anyone else needs to install it you'll need to go here [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) and click the download button. It will tell you that you need the new version to support this printer. Then follow the instructions.

When the sh installer gives the option to restart just unplug and plug it back in. The restart is confusing since it doesn't resume after restart. You'll have to look in Applications>accessories>HP Device Manager to run the setup.

---

