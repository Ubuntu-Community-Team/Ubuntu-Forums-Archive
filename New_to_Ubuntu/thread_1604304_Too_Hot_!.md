---
title: "Too Hot !"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by quilback on 2010-10-23
Howdy . I have a Toshiba M500  Duel boot 7-10.4  Windows runs cool but Ubuntu runs way to hot? It's like the fan wont kick in under this OS... Any suggestions would be greatly appreciated .    :)

---

### Post by Crusty Old Fart on 2010-10-23
Howdy quilback:

You might give this a shot:
Add the following boot option to your kernel:
   acpi=copy_dsdt

_Just in case you don't know how to do that, here's how:_
Open a shell (command line terminal)

Go to /etc/default with the following command:
```
cd /etc/default
```Make a copy of your grub file and name it grub_original just in case you need to revert to it:
       ```
sudo cp grub grub_original
```Edit the grub file:
       ```
sudo nano grub
```Locate the line that says:
       GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Change it to:
       ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=copy_dsdt"
```Press Ctrl+x to exit, then press y to save your changes, and finally press enter to write the file and leave the editor.

***** IMPORTANT *****
Run the following command to make your change propagate through the bootloader:
       ```
sudo update-grub
```That should do it (unless one of us has screwed something up).

In the event that you hose the grub file while editing it, you can replace it with the original that you made earlier and start over. Here's the command:
```
sudo cp grub_original grub
```Good luck.

(Ref.: [http://www.linuxquestions.org/questions/showthread.php?p=4129003#post4129003](http://www.linuxquestions.org/questions/showthread.php?p=4129003#post4129003))

---

### Post by Crusty Old Fart on 2010-10-23
Oh damn!

I forgot to tell you to reboot after all that.

See...this is the kind of jazz that happens with old age.

Sorry about that...Reboot.

---

### Post by wkhasintha on 2010-10-23
What exactly  does 'acpi=copy_dsdt' do? :confused:

---

### Post by quilback on 2010-10-24
Thanks for such a prompt reply. I will attack this tomorrow and share my results. Thanks again :)

---

### Post by Crusty Old Fart on 2010-10-24
_**[COLOR=Blue]To wkhasintha:[/COLOR]**_
    
Well...I'm not *exactly* sure how it works, but according to the  referenced link, acpi=copy_dsdt is supposed to enable the fan in Toshiba  laptops to be managed in such a way to turn on when the CPU begins to  get a tad toasty and to either throttle back or turn off when its wind  isn't needed anymore.
    
ACPI stands for "Advanced Configuration and Power Interface". It  replaced the old APM ("Advanced Power Management") about eight to ten  years ago. Both of them take part in managing power distribution. ACPI  is more advanced and can manage more power related features. It does  things like wake on LAN, suspend, hibernate, control fans,...that kind  of stuff.
    
I don't have a Toshiba laptop on which to test the "acpi=copy_dsdt"  kernel boot option. So I can't vouch for it. I reckon I should have  suggested that quilback check it out by reading more results from an  Internet search on it. But, I figured that's what any geek would do  before making code modifications that are new to them.
    
**_[COLOR=Blue]To quilback:[/COLOR]_**
    
You're mighty welcome. Hope it works. I'm going to see if I can edit my  post to clean it up a bit and embed the code pieces in their own blocks.  You'll have an easier time cutting and pasting if I can make that  happen in this forum software.

---

### Post by wkhasintha on 2010-10-24
> **Crusty Old Fart said:**
> [SIZE=2][FONT=sans-serif]_**[COLOR=Blue]To wkhasintha:[/COLOR]**_
    
Well...I'm not *exactly* sure how it works, but according to the  referenced link, acpi=copy_dsdt is supposed to enable the fan in Toshiba  laptops to be managed in such a way to turn on when the CPU begins to  get a tad toasty and to either throttle back or turn off when its wind  isn't needed anymore.
    
ACPI stands for "Advanced Configuration and Power Interface". It  replaced the old APM ("Advanced Power Management") about eight to ten  years ago. Both of them take part in managing power distribution. ACPI  is more advanced and can manage more power related features. It does  things like wake on LAN, suspend, hibernate, control fans,...that kind  of stuff.
    
I don't have a Toshiba laptop on which to test the "acpi=copy_dsdt"  kernel boot option. So I can't vouch for it. I reckon I should have  suggested that quilback check it out by reading more results from an  Internet search on it. But, I figured that's what any geek would do  before making code modifications that are new to them.
    
**_[COLOR=Blue]To quilback:[/COLOR]_**
    
You're mighty welcome. Hope it works. I'm going to see if I can edit my  post to clean it up a bit and embed the code pieces in their own blocks.  You'll have an easier time cutting and pasting if I can make that  happen in this forum software. [/FONT][/SIZE]

Thanx for the explanation bro:)

---

### Post by quilback on 2010-10-24
Hmm.  I have followed your detailed instructions three times exactly as explained . sadly to no avail :(   .The fan still stays quiet and the lappy heats up.. Any other suggestions @ Crusty Old Fart :)

---

### Post by Crusty Old Fart on 2010-10-24
Oh good...you tried it three times. That should make you really familiar with editing and updating grub.

There is another boot option that you can try. It is: acpi.power_nocheck=1

To add it to grub, you can follow the same steps as you did earlier, only your default kernel line would look like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=copy_dsdt acpi.power_nocheck=1
```Notice that I have left the  acpi=copy_dsdt option in there. At this point, we know that it didn't work by itself. Maybe  acpi.power_nocheck=1 would work by itself, or maybe both of them would be needed. So, there are only four possibilities to test, and we know that two of them don't work:

[LIST=1]
[*]Having no acpi options specifed <-- doesn't work.
[*]Having only acpi=copy_dsdt <-- doesn't work.
[*]Having both acpi options specified <-- needs to be tested.
[*]Having only  acpi.power_nocheck=1 <-- needs to be tested.
[/LIST]
You can test different combinations of kernel boot options by adding or removing them at the end of the default kernel line in the list that grub throws up on your screen during boot. Just press "e" to pause the bootloader and edit the selected kernel. Then type in your options at the end of the kernel line and finally press Ctrl+X to resume booting with the new options.

Understand that the changes you make with this method do not persist. They will only affect the current boot load. When you find a combination of options that work, you will need to edit grub, update-grub, and reboot as you did earlier.

A few final comments on all this. From my experience farting around with acpi kernel options (and believe me, I've done a LOT of it) they have never *broken* a system. So, I think we're safe experimenting with the ones we are playing with. I found them by reading other forums and bug reports. Some Toshiba owners experienced success with them. Others didn't. This whole fan problem fiasco seems to be a bigger problem on Toshiba laptops (most all recent variants) than on other hardware. However, it is NOT unique to Ubuntu. Suse, Fedora, Mint...several other distros aren't running the fans correctly on Toshibas. There is no doubt in my mind that there is some sort of glitch in the communication between Linux kernels and Toshiba laptop BIOS.

So...maybe we'll get lucky this time. Please test possibilities #3 and #4 above and let me know if you got lucky...thanks.

---

### Post by quilback on 2010-10-26
Toshiba Satellite M-500 Intel(R) core (TM) 2Duo CPU T6500@2.10GHz                                  Howdy "C,O,F"      
I have tried all of the specified methods you have described,and still the temp rises :(
I read in some forum that the actual BIOS might have to be updated?? Please enlighten :)  [ATTACH]173562[/ATTACH]

[ATTACH]173563[/ATTACH]
lsmod | grep acpi
lsmod | grep dev
modprobe toshiba_acpi

I haven't tried the above changes. Just wondering what you think about them? I will wait before attempting..

---

### Post by QIII on 2010-10-26
The "glitch" is that Toshiba defers fan management to the OS.  Do we think they did much work to make sure that this would work with an OS that holds a 2% market share?

I'll putter around a bit.  I know I've seen quite a bit written about this.  I don't know how many solutions I've read...

---

### Post by quilback on 2010-10-26
> **QIII said:**
> The "glitch" is that Toshiba defers fan management to the OS.  Do we think they did much work to make sure that this would work with an OS that holds a 2% market share?

I'll putter around a bit.  I know I've seen quite a bit written about this.  I don't know how many solutions I've read...
Thanks :)

---

### Post by Crusty Old Fart on 2010-10-26
Howdy quilback,

With regard to updating your BIOS:

[LIST]
[*]The BIOS program and any custom settings you have made to your BIOS configuration are stored in a CMOS chip. Your custom settings are maintained by having the chip powered  by a CMOS/BIOS battery. If the battery runs down, the system reverts to  using the default BIOS settings every time the PC boots. This is kind of nice because if you ever hose your BIOS settings so badly that your machine won't boot, you can remove the battery for a few seconds to force the CMOS to revert back to the original factory BIOS settings.
[/LIST]

[LIST]
[*]Updating the BIOS involves reflashing the CMOS chip. I've done it several times on different machines from the floppy drive. The process is fairly straight forward and I've never screwed it up. HOWEVER - If something goes wrong while attempting to reflash the CMOS chip, things could easily get jacked so badly that the computer will never boot again - EVER. So, it is not wise to reflash the CMOS chip as an experiment. It should only be done as a last resort, and only when you know exactly what your doing.
[/LIST]

[LIST]
[*]One of the nice things about floppy drives that make them so handy is that they run on their own controller having their own little operating system. So they can be used for really low level tasks, like reflashing CMOS, which is done before any of the larger "main" operating systems are loaded. Unfortunately, few computers are built with floppy drives anymore. That forces the job of reflashing CMOS to some other device. I think I've read somewhere that it can be done by making a bootable USB thumb drive. But, I've never done it that way. So, if we get to the point where you decide to reflash your CMOS, and you don't have a floppy drive from which to do it, I would suggest that you find an expert who has a history of success with the method you are considering. That person would NOT be me. I'm strictly a floppy flasher (Oh God! That sounds pretty bad...Did I really write that?...sorry...I hope the board moderators don't punt me for it.).
[/LIST]

[LIST]
[*]Assuming QIII is right about toshiba defering fan control up to the OS, then there probably ain't nuffin' to be gained by updating the BIOS anyway. But who the hell knows? This whole problem is a real stumper and the fixes I find on the 'nut don't work for everybody who tries them.
[/LIST]
Now...back to the Linux stuff:

[LIST]
[*]**lsmod** - is not a command that changes anything. All it does is list the status of modules in the Linux Kernel.
[/LIST]

[LIST]
[*]**grep** - stands for: Global Regular Expression Parser. It can serve to filter results from the standard output (stdout) from commands like lsmod. The symbol: **|** is called a pipe. Like a pipe, it allows things to flow from one place to another. So, the command **lsmod | grep *whatever*** takes the stdout from the lsmod command and *pipes* it into the grep command. Grep takes the data that's being fed to it by the pipe as its standard input (stdin), parses each line for the occurrence of the regular expression: *whatever* and outputs each line from the piped input that contained: *whatever*.
[/LIST]

[LIST]
[*]**modprobe** - is a command that runs a program to add or remove modules from the Linux Kernel (like drivers). It can do other things as well, depending on the options specified when it is invoked.
[/LIST]

[LIST]
[*]One of the best resources for teaching yourself Linux is the manual that comes bundled with most Linux distributions. Most Linux geeks call them: man pages. You can find out just about anything a command will and/or can do by studying its man page. For example, to learn about the command: modprobe, you would access its man page from the shell with the following command:```
man modprobe
```
[*]_You can navigate the man pages using the following keys:_
[/LIST]
[INDENT][INDENT]j <--moves down one line
k <--moves up one line
d <--moves down half a screen
u  <--moves up half a screen
f  <--moves down one full screen
b <--moves up one full screen
gg <--moves to the beginning of the man page
GG <--moves to the end of the man page
q <--closes the man page and returns to the command prompt[/INDENT][/INDENT]
[LIST]
[*]The command: **modprobe toshiba_acpi** would add the toshiba_acpi module to your kernel. Before you do that, it would be a good idea to find out whether or not it is already loaded, so that you could return your kernel to its current state if you wanted to undo any changes you made with the modprobe command.
[/LIST]

[LIST]
[*]_**Note:**_ after making changes to your kernel with modprobe, you'll have to reboot your machine to test their effect.
[/LIST]
Here's some code that you can cut and paste:[INDENT]To determine if the toshiba_acpi module is available in your installation:```
modprobe -l | grep toshiba_acpi
```To determine if the present state of you kernel is running the toshiba_acpi module:
```
lsmod | grep toshiba_acpi
```To add the toshiba_acpi module to the kernel:
```
sudo modprobe toshiba_acpi
```To remove the toshiba_acpi module from your kernel:```
sudo modprobe -r toshiba_acpi
```[/INDENT]Here's  another load of bummage for you. This time regarding how jacked even the toshiba_acpi module might be:
(Ref.: [http://memebeam.org/toys/ToshibaAcpiDriver](http://memebeam.org/toys/ToshibaAcpiDriver))
> 
 ***Please note:*** This driver is only intended to  provide the extra support for ACPI functionality specific to Toshiba  laptops.  In other words, this driver is not intended to cover standard  ACPI functions such as shutdown, reboot, suspend, hibernate, battery  info, etc.  Such generic functions are being supported by the ACPI4Linux  project [[1]]("http://acpi.sourceforge.net/") [[2]]("http://sourceforge.net/projects/acpi/") and the Software Suspend 2 project [[3]]("http://www.suspend2.net/") 
 ***Another important note:*** This driver does not  work on all Toshiba laptops, particularly those models which seem to  have a BIOS or other firmware which was not developed by Toshiba itself.   New reverse engineering work will have to be done on these machines,  or Toshiba will have to disclose the necessary details.  (For support of  machines with Phoenx BIOS, try the [[Omnibook driver]]("http://omnibook.sourceforge.net/").)  The error you will see in this case is: 
 
$ modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi
(.../kernel/drivers/acpi/toshiba_acpi.ko): No such device  The information on this page is only applicable to the latest version of the driver.I don't reckon there's much risk in testing the toshiba_acpi kernel module. Especially since you know how to remove it now. So, go ahead and give it a try if you want to.

One last thing, quil: If I'm hosing you down with too much elementary explanation, just tell me to bump your geektitude level up a few notches and I will assume you have more experience with Linux in future posts. In the meantime, I'll be looking for some of Santa's magic dust. We need that stuff right now. It's really great. It makes reindeer fly! Surely it could keep a little laptop cool.

Hasta la taco,

Crusty

---

### Post by QIII on 2010-10-26
There is a package called toshutils in Synaptic.

Unfortunately, if your BIOS only supports ACPI and not APM, this will not work.

Still digging.

Crusty Old Fart has given you some more to work on.

It must be great to be a Toshiba engineer.  Defer important functions to the OS rather than designing them yourself.

---

### Post by Crusty Old Fart on 2010-10-26
_[SIZE=1]**[COLOR=Navy]To QIII[/COLOR]**:[/SIZE]_

Yup...toshutils ain't going to be a happenin' thing here. APM was pretty much replaced by ACPI by the end of '02 or so.

As far as I've been able to determine, quilback's lappy is a model that is recent within the past three years or so. It knows about as much about APM as it does about penny candy.

I agree with you regarding the cotton-pickin' code cats at Tosh throwing their turds into the neighbor's garden instead of burying them in their own damned litter box...lazy S.O.B.'s

_[SIZE=1]**[COLOR=Navy]To quilback[/COLOR]**:[/SIZE]_

Can you get into your BIOS and tell us who wrote it and what version it is?

Also, can you tell us how old your lappy is?

You can look at one of the fixes I stumbled upon at the following link:
(Ref.: [http://sourceforge.net/apps/mediawiki/omnibook/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/omnibook/index.php?title=Main_Page))
I need to study up on this fix and get an idea of whether or not it has any hope of working before recommending it. Knowing how old your machine is, the BIOS version number and the company who wrote it (e.g.: Phoenix) would help us determine which solutions we might find on the 'nut may apply to your machine.

Thanks,

Crust

---

### Post by DooM55 on 2010-10-27
> **quilback said:**
> Howdy . I have a Toshiba M500  Duel boot 7-10.4  Windows runs cool but Ubuntu runs way to hot? It's like the fan wont kick in under this OS... Any suggestions would be greatly appreciated .    :)

Install the fan [COLOR=#000000]External lol this way work and very [/COLOR]Effective

:popcorn:

---

### Post by quilback on 2010-10-27
Whollygwakimollioes!! Lots of info to chew on thanks guys. Here is the audit you asked for.. This lappy is 2 years old ..:)

The level of description is perfect I am but a nubie

---

### Post by Crusty Old Fart on 2010-10-27
Thanks quil:

That was perfect.
 
[LIST]
[*]BIOS: American Megatrends Inc. 2.30 11/27/2009
[/LIST]
 So...we can pretty much forget about the Phoenix/Omnibook/Toshiba fix.

It may be helpful to know what kernel you're running. Please enter the following command and post the output in your next reply:
```
uname -r
```Let's find out what ACPI modules your kernel may be running. Please enter the following command:
```
lsmod | grep acpi
```Hopefully, your shell will just give you another input prompt without printing anything else to the screen.
If you get any output, it would probably be a good idea to ignore the rest of this post for now and just post the output in your next reply so we can take a look at what's running before we do anything else.

On the other hand...

In the event that you get no output, it means your kernel isn't using any ACPI modules and anything the kernel may be doing with ACPI is the result of the ACPI code that has  been compiled into the kernel. In this case, we can add the toshiba_acpi module if it is available in your version of Lucid.
So, let's find out if it's available with the following command:
```
modprobe -l | grep toshiba_acpi
```If it isn't available, your shell will just give you another input prompt without printing anything else to the screen. In this case, we should do some investigating to determine whether or not it would be safe to download it and install it before continuing.

On the other hand...
If you got some output that looks similar to this:
```
 kernel/drivers/platform/x86/toshiba_acpi.ko
```[COLOR=#006400][B]it may help to install the module with the following command:
[/B][/COLOR]```
sudo modprobe toshiba_acpi
```If you've gotten this far, it might be a good idea to issue the following two commands. They may be unnecessary, but they won't hurt anything if they aren't needed. If for some reason, there ends up being a code race between module loading and kernel modesetting (KMS), your poor little module could get run over by the KMS chariot. Updating initramfs will prevent that. Don't be surprised if the initramfs update takes a few seconds. The grub-update will run a little faster and is tossed in for good measure because I don't know if updating initramfs sometimes does things that need a grub update afterwards. So here they are:
```
sudo update-initramfs -k all -uv
sudo update-grub
```Now...Reboot.

After the machine has completely finished its boot, let's find out if the module got loaded. If it did, you should now get some output from the following command:
```
lsmod | grep acpi
```At this point, I'd like to see what the output is, if you don't mind posting it.
If you didn't get any output, then something happened that prevented the module from loading and you might want to repeat this process from [COLOR=#006400]**the bold, green text above**[/COLOR].

Next, assuming you had output indicating that the module is being used by the kernel, one of two possibilities will exist:
 
[LIST=1]
[*]You'll have a cool running happy     lappy...OR...
[*]You might want to think about asking DooM55 to send you a     very Effective External fan. I read somewhere that they're all the     rage in Syria.
[/LIST]
 I'll leave you with a couple of warnings against some of the things you may have read on other message boards about this problem:
 
[LIST]
[*]**DO NOT** add the kernel boot option: acpi=off to /etc/default/grub
[*]**DO NOT** add the kernel boot option: acpi=ht to /etc/default/grub
[/LIST]
[INDENT]Each of them will eventually cause thermal damage to your processor and you'll regret it.[/INDENT]That's about it for now.
Please let me know how it goes.

Crust

---

### Post by quilback on 2010-10-28
Am i doing something wrong ? 2.6.32-25generic

I get  a line saying Fatal error ?

Hmm I don't see any attachments

---

### Post by quilback on 2010-10-28
Trying to post attachments but no luck :(

---

### Post by Crusty Old Fart on 2010-10-29
Thanks for posting the kernel version.
> I get a line saying Fatal error ?Ahhh...you made it all the way through the instructions to where you were trying to install the module. Good.

The only command that I know of in my last post that could have given you a fatal error would have been:
```
modprobe toshiba_acpi
***Output:***
FATAL: Error inserting toshiba_acpi 
(/lib/modules/2.6.32-25-generic/kernel/drivers/platform/x86/toshiba_acpi.ko): 
Operation not permitted

```You see the last part of the error says: Operation not permitted. That was my fault. A thousand apologies, quil. I forgot to preface the command with **sudo** to allow root privileges. The command should have been:
```

sudo modprobe toshiba_acpi

```I've gone back and edited my last post to reflect the correction.

However, there is a possibility that even with the sudo prefix, this could happen:
```
sudo modprobe toshiba_acpi
***Output:***
FATAL: Error inserting toshiba_acpi 
(/lib/modules/2.6.32-25-generic/kernel/drivers/platform/x86/toshiba_acpi.ko):
No such device

```You see the last part of the error says: No such device. That means that your BIOS is NOT compatible with the toshiba_acpi module that is included with your kernel source. So, it wouldn't load, even though it was available. No harm done. Just time wasted as we learned that another solution won't work for you. When you wrote that your BIOS was written by *American Megatrends Inc.*, I knew that use of the toshiba_acpi module might be a long shot because of what we learned from the quote I put in this post: [Number 13 of this thread]("http://ubuntuforums.org/showpost.php?p=10031790&postcount=13")

Soooooo...what's a freakin' geek to do? We're striking out every time we pick up a bat and your laptop is still getting hotter than nickel-night in the whorehouse.

_With regard to your posting problems:_

You should be able to copy and paste from your shell to this forum.

I don't know what would be causing your attachments to fail. If I were you, I would delete my browser cache and cookies, and restart my browser. That has often fixed the features on a website that have gone south for me, especially when a script has been broken.

Anyway...there's some other stuff I'm looking at, but it involves a whole bunch of advanced geekology that could probably get you into a boatload  of trouble if you started mucking around with it without an expert sitting next to you to guide you through the process. I don't think you'd cotton too much to the idea of me telling you that we need to decompile your DSDT tables, edit them, and recompile them, as well as re-flashing CMOS.

That laptop you have is a VERY impressive machine. When I read through the specs that you attached for it, I could hardly believe what a powerhouse it is. If I were you, and I liked Windows 7 (which I hear most people do), I don't think I'd run any Linux OS on it anymore. I'd hate to learn that all this experimentation ended up finally cooking your processor so badly that its little brains had been fried forever. One of the nice things about Linux, and especially Ubuntu, is that it will run on a lot of very old hardware. I encourage you to continue learning Linux/Unix because it's great stuff. But, it ain't worth toasting an expensive laptop if you can get your hands on an old one. There should be plenty of them floating around for really cheap prices, now that Windows 7's minimum system requirements have pretty much rendered all laptops older than two years of age to the ash heap of technological advancement.

Sorry to have put you through all of this without it ending in success. As far as possible solutions go, we've picked all the low hanging fruit that I could find out there. If you run across something that looks like you might be interested in trying, feel free to post it here and I'll take a look at it if you want my comments. But, for now, I'm out of bullets.

It's been a pleasure meeting you here, quil.

Good luck with the mess. Please don't fry your computer.

Take care,

Crust

---

