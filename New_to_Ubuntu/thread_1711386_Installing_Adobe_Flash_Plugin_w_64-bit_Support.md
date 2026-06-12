---
title: "Installing Adobe Flash Plugin w/ 64-bit Support?"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Valkyr333 on 2011-03-21
Hi everyone,

I'm trying to install the Adobe Flash Plugin with 64-bit support for my Firefox Browser. I'm using the 64-bit version of Ubuntu Lucid, hence that's the one I went for. Thing is, apparently they haven't released anything but a test/sample version of this 64-bit support plugin, "Adobe Square" and it's only available as a tar.gz. I'm completely unfamiliar with these and I've read in the Ubuntu documentation that while it's actually a simple process when you know what you're doing, compiling software *can* be dangerous to a Linux Installation, so I'm hoping maybe someone here can tell me the safest way to do this?

Thanks,

-Val

---

### Post by Arijit_Kundu on 2011-03-21
Have a look [here]("http://ubuntuforums.org/showthread.php?t=772490")

---

### Post by gandaran on 2011-03-21
install the [firefox flash-aid addon]("https://addons.mozilla.org/en/firefox/addon/flash-aid/") to help you correctly remove and install the flash plugin.

---

### Post by grahammechanical on 2011-03-21
I am using 64bit Ubuntu and the Ubuntu software Centre has an Adobe Flash Plugin installer and Adobe flash plugin 10 for Maverick. I installed the latest Adobe Flash this way. I am less nervous when using the software Centre or Synaptic than compiling the source code.

Regards.

---

### Post by wizard10000 on 2011-03-21
> **Valkyr333 said:**
> Hi everyone,

I'm trying to install the Adobe Flash Plugin with 64-bit support for my Firefox Browser. I'm using the 64-bit version of Ubuntu Lucid, hence that's the one I went for. Thing is, apparently they haven't released anything but a test/sample version of this 64-bit support plugin, "Adobe Square" and it's only available as a tar.gz. I'm completely unfamiliar with these and I've read in the Ubuntu documentation that while it's actually a simple process when you know what you're doing, compiling software *can* be dangerous to a Linux Installation, so I'm hoping maybe someone here can tell me the safest way to do this?

Thanks,

-Val

Here's an easy way to do it - you can add the repository below and just install it that way:

```
sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

```

Note this will remove your current 32-bit Flash but I've been using 64-bit Flash since well before Adobe took it offline the last time and haven't had any issues.  The current version seems to work fine.

Hope this helps -

---

### Post by oldos2er on 2011-03-21
> **grahammechanical said:**
> I am using 64bit Ubuntu and the Ubuntu software Centre has an Adobe Flash Plugin installer and Adobe flash plugin 10 for Maverick. I installed the latest Adobe Flash this way. I am less nervous when using the software Centre or Synaptic than compiling the source code.


Flash is closed-source proprietary, so in this case there's no source code to compile, just copy libflashplayer.so to ~/.mozilla/plugins

64-bit flash is not in the repositories; what you have is 32-bit flash with nspluginwrapper.

---

### Post by Valkyr333 on 2011-03-21
> **wizard10000 said:**
> Here's an easy way to do it - you can add the repository below and just install it that way:

```
sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

```Note this will remove your current 32-bit Flash but I've been using 64-bit Flash since well before Adobe took it offline the last time and haven't had any issues.  The current version seems to work fine.

Hope this helps -

Okay, that's done but now instead of asking me to upgrade my Adobe Flash Plugin on pages like YouTube, I get the little lego-block-sadface icon and the message, "The Adobe Flash plugin has crashed." It gives me the option to submit a crash report, and to reload the page and try again, but reloading produces the same results. I also get the same error icon when using flash-dependent add-ons like FoxTab. My first instinct here is to reboot and try again, but given my past dealings with this method in Linux, I feel inclined to ask if there's much of a chance this will make things worse?

*Update - Update Manager required a restart, and I went with it. At this point, FoxTab seems to be working great. However, I'm still getting flash-crash messages from YouTube.

---

### Post by Cracklepop on 2011-03-22
> **Valkyr333 said:**
> Hi everyone,

I'm trying to install the Adobe Flash Plugin with 64-bit support for my Firefox Browser. I'm using the 64-bit version of Ubuntu Lucid, hence that's the one I went for. Thing is, apparently they haven't released anything but a test/sample version of this 64-bit support plugin, &quot;Adobe Square&quot; and it's only available as a tar.gz. I'm completely unfamiliar with these and I've read in the Ubuntu documentation that while it's actually a simple process when you know what you're doing, compiling software *can* be dangerous to a Linux Installation, so I'm hoping maybe someone here can tell me the safest way to do this?

Thanks,

-Val

It's actually extremely simple:
.tar.gz is like a .zip file - right click it and select 'extract here'
you'll get a .so file - put it in ~/.mozilla/plugins 

That's it. All done.
Note that you will have to select View > Show Hidden to be able to see the .mozilla folder, and if there isn't a plugin folder inside it just make one yourself.

---

### Post by klirka on 2011-03-24
hello, it seems i have to update to a new flash version? i cannot watch any videos any more.
i installed the flash-aid add-on in firefox. under "removal options" i see nothing until i select "expert mode". i have attached a screenshot. what do i need to select there and what are the next steps?
i just upgraded to firefox 4.0, on kubuntu10.10.
thank you!

---

### Post by Valkyr333 on 2011-03-24
Wizard10000's idea turned out to fix the issue. It was shaky/screwy at first but then became surprisingly stable. At the moment it works great, so I'm marking this thread as "Solved."

*Klirka - You might want to start your own thread when it comes to your issue. I'm no expert, but it sounds like a different issue than the to which I was referring. Best of luck!

-Val

---

### Post by klirka on 2011-03-24
no problem, i started a new thread.

---

