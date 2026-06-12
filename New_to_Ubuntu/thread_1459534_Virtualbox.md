---
title: "Virtualbox"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-21
I'm going to be using virtualbox to run Windows Vista and play around with photoshop there since I'm having difficulty getting it onto Ubuntu. Things like this don't seem uncommon for Linux users.

I have a silly question. I've got Virtualbox working and installed Vista onto my Virtual Computer. Now, do I need to install drivers for it? It seems to be running just fine. Is it working with the same information that Linux uses to cooperate with the hardware?

---

### Post by empty_spaces on 2010-04-21
Do you have virtualbox guest additions installed? They will ensure that Vista plays nice with the virtual hardware of virtualbox.

---

### Post by anewguy on 2010-04-21
If you mean do you have to install Windows drivers to your "new" Vista install in VirtualBox, the answer should be no.  The same goes for the "motherboard drivers" that are often included on a CD or other media.  The devices are virtualized Linux devices and should be accessable.  If things like a USB connected printer, etc., aren't showing, be sure you installed the PUEL version of VirtualBox so that you get USB support.  When you have that, you need to set at least one filter to allow USB devices, then select them from the bottom bar of the virtual machine window.  Also, networking is different - you can set this up on the VirtualBox main screen and going through the options for your virtual machine.

Dave ;)

---

### Post by orphanlast on 2010-04-21
Hey thanks guys. I've had it working on my computer for a little while now and I've been timid on using it because computers act really freakin' stupid if they don't have drivers... and I didn't want to install the drivers if I didn't have to.

Thanks!

:)

---

### Post by orphanlast on 2010-04-21
I do however have one last question. I keep being stupid and keep shutting down the virtual computer improperly... I need to get used to the fact that you just can't close the window. You have to close windows itself. 

... So it keeps asking me if I want to close it on safe mode. Do you think that it's really a big deal? Is it possible that the virtual computer may be fragmenting the windows information and that this could lead into future problems if I don't make sure to close windows properly every single time?

---

### Post by _0R10N on 2010-04-22
In my personal experience, not closing the virtual machine appropiately may lead to the loss of information. I once had to install one with XP because I was working in a project that used MSSQL Server, and sometimes (I mean after some crashes) changes I had made on my code (I was using eclipse) weren't there.

I couldn't tell exactly if fragmentation, or any other thing related, takes place, but it's always a good practice to turn off the virtual machine the way it should.

Kind regards!

_0R10N >>

---

### Post by asharpham on 2010-04-22
I agree. I have WinXP running very successfully in a VirtualBox and it's always best to close it the same way as you would if you were running Windows as your main OS. If I try and close it in another way (like clicking the cross at the top right instead of shutting down properly), I get a VirtualBox prompt giving me 3 options for shutting down. Maybe Vista isn't so forgiving.

---

### Post by shebaw on 2010-04-22
One last tip, since your going to run Windows on a virtual machine it would be a great idea to take a snapshot of it now and you can revert back to this snapshot if/when something goes wrong(viruses, BSODs and the like).

---

### Post by orphanlast on 2010-04-23
> **shebaw said:**
> One last tip, since your going to run Windows on a virtual machine it would be a great idea to take a snapshot of it now and you can revert back to this snapshot if/when something goes wrong(viruses, BSODs and the like).


How would you go about doing that? Is it just something simple with clicking on a few menus?

---

### Post by mikodo on 2010-04-23
> **orphanlast said:**
> How would you go about doing that? Is it just something simple with clicking on a few menus?
It has been a while since I have had Vbox installed. If I remember correctly, when you open the VBox application, on the left where it indicates the vm's that are installed, (in your case Vista), if you click on the space that indicates which vm you intend to use, in effect making whatever you are calling the vm, become highlighted. Then go to the top of that area and to the right towards centre and you will see buttons that include taking a snapshot. Click on that and you are done, following the same procedure will produce another. Careful though, each snapshot takes up space. You can also take snapshots while the vm is running, but I have forgotten how to do that. Maybe someone else will chime in to tell you how to take snapshots while using the vm

Good Luck!

---

