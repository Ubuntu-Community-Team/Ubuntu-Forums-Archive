---
title: "can't upgrade VirtualBox from 3.2 to 4.0"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by s1baker on 2011-05-28
Hi,
I have received a notice that VirtualBox has an upgrade - 4.0, but when I downloaded the deb file, after the file is downloaded I get the notice that it conflicts with 3.2 and it will not go ahead and complete the install.

I have Ubuntu 10.10 with 32 bit.

Does anyone know why there is a conflict of 4.0 with 3.2 VirtualBox?

Thanks

---

### Post by rvchari on 2011-05-28
> **s1baker said:**
> Hi,
I have received a notice that VirtualBox has an upgrade - 4.0, but when I downloaded the deb file, after the file is downloaded I get the notice that it conflicts with 3.2 and it will not go ahead and complete the install.

I have Ubuntu 10.10 with 32 bit.

Does anyone know why there is a conflict of 4.0 with 3.2 VirtualBox?

Thanks

you can simply remove virtualbox3.2 and install ver 4.0 using deb installer. your settings from 3.2 can be used in 4.0 so long as your .files in home folder is intact.

i had done that and reverted back to 3.2

---

### Post by Paqman on 2011-05-28
Remove 3.2, then install 4.0.

---

### Post by Paddy Landau on 2011-05-28
> **s1baker said:**
> Does anyone know why there is a conflict of 4.0 with 3.2 VirtualBox?
I don't know *why*, but as the other posters said, all you need do is uninstall all versions and then install the latest (4.0.8 from the official website). You might want to install the optional extensions, too. You shouldn't lose any data on the upgrade.

---

### Post by s1baker on 2011-05-28
But won't removing 3.2 destroy all the files and programs I have put in VB?

---

### Post by s1baker on 2011-05-28
also, how should I go about removing 3.2?
thanks

---

### Post by Paqman on 2011-05-28
> **s1baker said:**
> But won't removing 3.2 destroy all the files and programs I have put in VB?

Nope. They're all kept safe in your home folder. You *can* uninstall it in a way that will dump all that data, but that's not the default behaviour.

Just open up Software Centre, search for your Virtualbox under "Installed software" and click "remove".

---

### Post by rvchari on 2011-05-28
> **s1baker said:**
> But won't removing 3.2 destroy all the files and programs I have put in VB?

all ur os options in prev version can be taken by 4. you have to point the vdi file and configure to boot from there thats it..

---

### Post by beew on 2011-05-28
If you install VB 4.0 with a PPA then you don't have to uninstall anything, you can just upgrade it in Synaptic.
[http://www.unixmen.com/software/1525-virtualbox-404-is-released-ppa-debian-and-ubuntu](http://www.unixmen.com/software/1525-virtualbox-404-is-released-ppa-debian-and-ubuntu)

This link came out in Feb, I think now you can simply enable Oracle's ppa.

---

### Post by s1baker on 2011-05-28
I removed 3.2  and downloaded the 4.0.8, but now I get the
message in Ubuntu Software Center

Internal Error, The File "tmp/virtualbox-4.0_4.0.8-71778-Ubuntu~maverick_i386.deb" could not be opened.

---

### Post by Paddy Landau on 2011-05-28
> **s1baker said:**
> I removed 3.2  and downloaded the 4.0.8, but now I get the
message in Ubuntu Software Center

Internal Error, The File "tmp/virtualbox-4.0_4.0.8-71778-Ubuntu~maverick_i386.deb" could not be opened.
Did you download 4.0.8, or try to install through the PPA?

beew is absolutely correct; you don't have to download, you can add the PPA.

Here is what I suggest.

[LIST=1]
[*]Uninstall _all_ versions of VirtualBox. You may find Synaptic better than Ubuntu Software Centre for this.
[*]Add the PPA to your repositories (go to the [Linux download page]("http://www.virtualbox.org/wiki/Linux_Downloads"), scroll down to *Debian-based Linux distributions*, and follow the instructions).
[*]You cannot install the guest additions from the repositories (strangely), but you can download them from the website (go to the [download page]("http://www.virtualbox.org/wiki/Downloads") and scroll down to *VirtualBox 4.0.8 Oracle VM VirtualBox Extension Pack*).
[/LIST]

---

### Post by s1baker on 2011-05-28
Thanks Paddy Landau & everybody.

For some reason, Ubuntu Software Center downloaded the 4.0.8 version, but where it put it on my system, I don't know ( did a search in all the files but could not find it )
Anyway, I manually downloaded the file into a folder of my choosing and installed it from there. Got the extensions also. As an aside, the extensions will now let me use my USB SD disk, ( wouldn't do that before with 3.2 )

Will mark this resolved now

---

