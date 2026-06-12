---
title: "Put old computer into Virtual Box?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Aussieartist on 2008-12-26
Hi all, 
This is a bit of a challenge... I've got my Ubuntu 8.10 running great, I've got Virtualbox running great too (Thanks to the patience and assistance of people in this forum)... I should have done it years ago...

Now I'm wondering if there is a way to install my old computer's copy of XP with all the apps, settings and tricks etc into a Virtualbox partition... I can dump the whole old c drive onto a USB drive and copy it to the new machine... but of course Virtualbox doesn't see the registry and other magical faries that were in the old machine. Bear in mind I have been using the old machine with XP for 5 years and have all the software and things tweeked just the way I want them them.

Has anyone ever done an exact clone of an old computer into a new Virtualbox partition and made it work? Or am I asking the impossible?

Thanks
Aussie:)

---

### Post by markharding557 on 2008-12-26
it will be intresting to see what happens so give it a go.
possibly different hardware will cause problems

---

### Post by Shazaam on 2008-12-26
As stated by the previous post Windows drivers will be an issue that CAN be solved. Many posts/tutorials are out there that will help with driver problems.
Since VBox will run VMware .vmx and .vmdk files I recommend VMware Converter. This will make a virtual machine out of your XP install that VBox should run. If you do a search of the VMware site you will find out the pro's and the pitfalls of doing this. Once you get XP converted, depending on the size, you could probably transfer it to your Ubuntu box via usb or dvd.
One thing to remember, you will have to re-validate the virtual XP which will invalidate the original XP install per Microsoft.
Some links for you...
[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)
[http://ubuntuforums.org/showthread.php?t=380699](http://ubuntuforums.org/showthread.php?t=380699)
[http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround](http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround)

---

### Post by Aussieartist on 2008-12-29
I ended up giving the whole idea some serious thought and decided I was seeking the answer to a question I didn't really need to ask...

(Not to say others don't need the solution)

I did a new install from my old XP CD... it's not a real solution to the original post but the up-side is I didn't have to bring all the ugly stuff over to my new XP VM and consequently have a faster system. I'm now selectively installing the software I REALLY need... without the junk!

It also gives me reason to use Ubuntu OS more and try alternative apps.

I guess it's the Zen answer...
Cheers
Aussie

---

### Post by scorp123 on 2008-12-29
> **Aussieartist said:**
>  Now I'm wondering if there is a way to install my old computer's copy of XP with all the apps, settings and tricks etc into a Virtualbox partition...  You mean like this?
[http://forums.virtualbox.org/viewtopic.php?p=48012&sid=f0f39e59853532327af971e9cf077248](http://forums.virtualbox.org/viewtopic.php?p=48012&sid=f0f39e59853532327af971e9cf077248)

Apparently there is a tool from VMware that will convert a real XP installation into a VMware *.vmdk image (to be used with VMware). But VirtualBox happens to understand that file format as well.

---

### Post by scorp123 on 2008-12-29
> **shazaam said:**
>  since vbox will run vmware .vmx and .vmdk files i recommend vmware converter. This will make a virtual machine out of your xp install that vbox should run.  +1

---

