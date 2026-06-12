---
title: "Removing installed from Wine"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-05-19
I've tried several different methods to remove an installed package from Wine but have failed miserably. Here's the info on what I've done so far:

Downloaded PCSuite for my Sony Ericsson W760 from their site so I would have it on cd and available in a desktop folder, if needed.

Started with wine and installed the Sony Ericsson PCSuite so I could connect the phone to the update service and use the phone to connect to the 'net. No matter what I did when I plugged in the phone the FStop would jump on screen regarding the photos, but that is all that would work in connecting the cell via USB. There would also be an "Unable to mount W760 - Error 60" box pop up. Figured I'd uninstall from Wine and start over. No good. Would not continue past first removal page.

Tried "Uninstall Wine Software": waited 10 minutes or so.Never got past first page for the uninstall. Had to restart to get that off the screen.

Removed everything I could find related to PCSuite. Still appeared in Wine

Did total uninstall of Wine. Shutdown for a few minutes, Restarted and reinstalled Wine. Checked Wine programs and PCSuite no longer listed. Thought it might work if I went into Uninstall Wine Software option because it also offers Install option. Found PCSuite still showing there. Clicked on remove and window pops up offering removal but stops there. Had to shutdown and restart to get rid of it again.

Any ideas on how to get the PCSuite out of the "system" entirely?

Note: Also installed PCSuite in VBox under WinXP, to see if that would work, but cannot get USB connected there either. Any suggestions on how to correct that problem?

EDIT: Also noticed that when the cell phone was plugged in a box would pop up with "Wired network disconnected" and the Wi-Fi indicator on the top bar would reset. Does that help in figuring this out?

---

### Post by Paddy Landau on 2010-05-19
Uninstalling and reinstalling a program won't do anything. (This isn't Windows!)

Instead, I would do this.

Delete the directory [FONT=Courier New].wine[/FONT] from your home folder. That will make as if wine had never been used.

Then install [PlayOnLinux]("http://www.playonlinux.com/") (I think it's in the repository). PlayOnLinux is a front-end for Wine, making it easy to install, run and uninstall Windows programs (using Wine).

Install your program using PlayOnLinx. Then see whether it works.

To uninstall, use PlayOnLinux, which will remove all traces of PCSuite, without affecting any other programs that you've installed with PlayOnLinux.

Bear in mind that not a high proportion of Windows programs will run under Wine. You may have to settle for dual-boot in order to access your phone using PCSuite.

The alternative is to not use PCSuite, and just access the phone as an external memory stick. That works well for me with my Sony Ericsson.

---

### Post by flyfishingphil on 2010-05-20
> **Paddy Landau said:**
> Uninstalling and reinstalling a program won't do anything. (This isn't Windows!)

Instead, I would do this.

Delete the directory [FONT=Courier New].wine[/FONT] from your home folder. That will make as if wine had never been used.

Then install [PlayOnLinux]("http://www.playonlinux.com/") (I think it's in the repository). PlayOnLinux is a front-end for Wine, making it easy to install, run and uninstall Windows programs (using Wine).

Install your program using PlayOnLinx. Then see whether it works.

To uninstall, use PlayOnLinux, which will remove all traces of PCSuite, without affecting any other programs that you've installed with PlayOnLinux.

Bear in mind that not a high proportion of Windows programs will run under Wine. You may have to settle for dual-boot in order to access your phone using PCSuite.

The alternative is to not use PCSuite, and just access the phone as an external memory stick. That works well for me with my Sony Ericsson.
Paddy,

Must have forgotten to hit the reply button this morning when I was getting ready to hit the road. Thanks for the advisory. Was just wondering how you got it to work as an external memory stick. The only "offer" I received was from F-Spot to open the photos.

Now that I've arrived, and had a chance to go back over your message it raises a few more questions.

I went into my Home folder and see no listing in there anywhere of Wine. (Also nothing relating to the SE W760.) Since Wine came in the 10.04 download, at least I thnk it did because I don't remember installing it, what else might work? I don't see it listed anywhere but in the usr/bin, along with a lot of others. Wondered if that shows the Synaptics list or something because I don't remember doing anything with most of what is listed there.

I am seriously looking at doing another format, installing XP Pro (that's what SE prefers, along with Magellan and a couple of other things) and see if I can set up share folders so I can move stuff bck and forth without having to transfer to a USB memory stick or something like that. I'd only need to use the XP when I had to get on line while "on the road". (Usually it happens when I'm out fishing and somebody wants to buy a rod from me.)

I'll be traveling for a couple of days but I'll check out my thread before I leave in the morning and as soon as I get to the next lodging in the evening.

Thanks again for the assist.

---

### Post by Paddy Landau on 2010-05-20
> **flyfishingphil said:**
> Was just wondering how you got it to work as an external memory stick. The only "offer" I received was from F-Spot to open the photos.
F-Spot is the default application for that sort of thing. I don't like F-Spot. Simply press Cancel (or whatever button that tells the dialogue to go away).

Your Sony Ericsson should be set up to use "mass storage memory" (well, that's what my phone calls it) when using USB.

On your computer, the phone memory should mount as an external USB drive. If you have a memory card in the phone, that will mount as a second drive.

Remember to *unmount* or *safely remove* both of them before you disconnect the phone.

> **flyfishingphil said:**
> I went into my Home folder and see no listing in there anywhere of Wine.
Careful. The directory has a point in front of it:
[FONT=Courier New].wine[/FONT]
If you are in Nautilus, press Ctrl-H (or View > Show Hidden Files) to be able to see files that start with points. If you are in terminal, use [FONT=Courier New]ls -lA[/FONT] to see them.

> **flyfishingphil said:**
> I am seriously looking at doing another format, installing XP Pro (that's what SE prefers, along with Magellan and a couple of other things) and see if I can set up share folders so I can move stuff bck and forth without having to transfer to a USB memory stick or something like that. I'd only need to use the XP when I had to get on line while "on the road". (Usually it happens when I'm out fishing and somebody wants to buy a rod from me.)
Yes, that is one way. If you set up both Windows and Ubuntu on your computer as a dual-boot, you can certainly do that.

PCSuite would store all the data on Windows. By default, Ubuntu can easily read and write your Windows partition, so sharing won't be a problem. Be aware that while Ubuntu can see your Windows partition, Windows cannot see your Ubuntu partition.

It does mean that whenever you want to use PCSuite, you'll need to restart the computer to boot into Windows, then when you've finished, restart to start Ubuntu. Unless, of course, your computer can cope with running Windows in a virtual machine under Ubuntu, but you said that you had problems with that.

---

### Post by flyfishingphil on 2010-05-20
> **Paddy Landau said:**
> F-Spot is the default application for that sort of thing. I don't like F-Spot. Simply press Cancel (or whatever button that tells the dialogue to go away).

Your Sony Ericsson should be set up to use "mass storage memory" (well, that's what my phone calls it) when using USB.

On your computer, the phone memory should mount as an external USB drive. If you have a memory card in the phone, that will mount as a second drive.

Remember to *unmount* or *safely remove* both of them before you disconnect the phone.


Careful. The directory has a point in front of it:
[FONT=Courier New].wine[/FONT]
If you are in Nautilus, press Ctrl-H (or View > Show Hidden Files) to be able to see files that start with points. If you are in terminal, use [FONT=Courier New]ls -lA[/FONT] to see them.


Yes, that is one way. If you set up both Windows and Ubuntu on your computer as a dual-boot, you can certainly do that.

PCSuite would store all the data on Windows. By default, Ubuntu can easily read and write your Windows partition, so sharing won't be a problem. Be aware that while Ubuntu can see your Windows partition, Windows cannot see your Ubuntu partition.

It does mean that whenever you want to use PCSuite, you'll need to restart the computer to boot into Windows, then when you've finished, restart to start Ubuntu. Unless, of course, your computer can cope with running Windows in a virtual machine under Ubuntu, but you said that you had problems with that.
Merci Beaucoup! Muchas Gracias! You're directions just added a major step forward in my understanding of how to do some of the "stuff" in here. I can play around with this a bit and see "what happens if I ...?" before I make my final decision. I'll try plugging in the SE and, if that works, no need for the XP.

I'll mark this as solved for now. If there are any more problems I'll start another thread. Thanks again

---

