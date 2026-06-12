---
title: "Just So That You know - VirtualBox &amp; 2nd OS"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by oldefoxx on 2009-08-31
You decide to give Ubuntu a try, and you like it well enough, but for some reason decide not to give up on Windows.  Maybe because it is the only to be able to run some of your faqvorite games, or maybe you decide to stick with your present email client and your history of filed emails and addresses.  Dual booting and choosing between two or more OSes sounds feasible enough, but that means a complete reboot each time you want to go from one to the other.  So is there a better or alternate way, aside from having to buy a second PC?

Several ways, such as using a smart card with the second OS installed or a plug-in external drive that you can alternately boot from.  Still, you have to reboot to have the advantage of the second OS.  So can you have both running at once?  And the answer to that is "yes".

VirtualBox is a Virtual Machine Manager, meaning that it creates a virtual environment for the second OS to run in.  There are a number of VM Managers out there to choose from, but I like VirtualBox, even though it is not ideal or perfect.  However, it is getting better with each new release.  Sun Microsystems bought out the company that created VirtualBox, so use Sun VirtualBox in your search.  There is also an Open Source Edition (OSE) of VirtualBox, but the Sun version is easy enough to enable USB support in it, but you have to look for posts regarding both VirtualBox and USB to get more details.

Seems like every time I update VirtualBox, something gets fixed, but something else goes awry.  It helps to publish bug reports when you find something not quite right, but no guarantee when it will be addressed.

After you install VirtualBox, you will need to create a new client environment, consisting of RAM, hard drive space, and various peripherals (network access, sound, things like that).  You do all those things under Settings.  When you start your client, there will be nothing on the virtual drive, meaning you have to have an OS install image (ISO) or CD disk to boot it from, then go through the install process.  I like Windows 2000 for this, but others have used XP and Vista, or even a different version of Linux.

When I first got started with Ubuntu and VirtualBox, I could not get the client to boot from the real CD Drive.  It worked well enough with an ISO image, so I used some of the client software in Ubuntu to first copy the install CD to an ISO file on the hard drive, then used that.  It worked well enough, and later I switched the CD reference to the VBoxGuestAdditions.iso and ran that after installing Windows.  That makes changes that helps Windows work better as the client.

Now I have another new problem.  I can get VirtualBox to boot from the install ISO for Windows, but I've tried to get other install CDs and ISOs to boot instead, and VirtualBox tells me that none of these is bootable.  I want to boot Acronis True Image 11 Recovery Disk to see if I can just restore a prior backup of the client side rather than make it all over again, and it is refusing to perform the boot.  I mean I can perform a real live boot with any of these CDs, no problem, and yet VirtualBox is flaunting my efforts to do the same on the client side.

A boot ISO is a boot ISO is a boot ISO if you know what I mean, and there must be some3thing going on here that I don't know about.  Please enlighten me if you can and tell me how to get around this problem.

---

### Post by oldefoxx on 2009-08-31
I used Brassero Disk Burner and was able to copy a CD image to an ISO file on the Desktop and run it on the client side, but I ran into another issue is that I could not then access a .TIB file to restore its image to the client.  Not possible, because to access this file, the drive has to be made accessable via shared folders or as a USB device.  To do either, you haveto have something like Windows installed first as a means of enablement.

So while I should eventually get True Image to work on the client side, it seems I have to first install Windows, use the VBoxClientAdditions to get decent color and resolution, copy the needed .TIB file to a folder or drive that can be shared or accessed via USB, install or use the Acronis software, access the .TIB file, and hope that I can run a complete backup install from the .TIB file before something screws up.  I suspect that this will prove improbable or impossible.

Not too promising a prospect.  Using the True Image Recover method by itself in client mode is not capable enough, as it is unable to see either USB drives or shared folders, at least not as reference by VirtualBox on the client side.

---

### Post by Mark Phelps on 2009-09-01
> **oldefoxx said:**
> I want to boot Acronis True Image 11 Recovery Disk to see if I can just restore a prior backup of the client side rather than make it all over again, and it is refusing to perform the boot.

A boot ISO is a boot ISO is a boot ISO if you know what I mean, and there must be some3thing going on here that I don't know about.  Please enlighten me if you can and tell me how to get around this problem.
You do realize that the Acronis boot CD is actually a Linux boot CD, right? (That is, unless you built your own using BartPE -- and you didn't mention that) 

It could be that you can't boot a Linux boot CD inside of Virtualbox -- don't know.

---

### Post by oldefoxx on 2009-09-01
Yes, I was aware of tht.  But the CD boot method is fairly standard.  I played with the issue today, and found that I could copy a bootable CD to an ISO file, then tell VirtualBox to boot from the image, and it does work.  Just won't boot from the original CD.

Beyond that, I designated a second client as Windows 2000, but elected instead to format with and install Windows XP there.  No problem, and I then installed Acronis True Image 11 on that client, and then enabled VirtualBox to work with USB devices, and enabled the External USB drive to be passed to the client.  I grabbed the VDI.tib file and had it restore all folders and files to their original locations on the local C drive.  Everything went fine, and I now have Windows 2000 Pro in place of Windows XP Pro, and everything back on the local C drive.  No problems there, so it does work.

Next I just set up the USB for access by the first client, then tried to use the Acronis True Image Recovery CD image instead of installing an OS or Acronis directly.  This time I chose to restore the whole local C drive partition, and this is also working.  So my concerns as to whether either would fail were misplaced.  And this method also gives me a clone of the client, which may prove useful later.

Most hints on doing Linux bckups and restores rely on the tar method, and that can work, but while Acronis must install and run under Windows, and the Recovery method relies on a variation of Linux, it's posible to back up non-FAT and non-NTFS drives ande partitions using it.  To access non-FAT and non-FTFS drives with Windows, you can search for and find utilities that add this capability to Windows.  Linux on the other hand can use a special set of drivers that go by ntfs-3g to handle Windows drives and folders.  But when using Windows as a VirtualBox client, Windows has access to the various partitions and drives via VirtualBox, which then has the resources of the host to draw upon.  So partitions, folders, files with either system can be accessed and used by the other system.  Now that is hard to beat!  Snf you vsn sldo tske screen snspdhotd of either side and do cut and paste or copy and paste between applications on both or either side.  That an be extremely convenient as well.

---

### Post by oldefoxx on 2009-09-02
You might well wonder why the jump to XP, then revert to 2K.  XP is a fine OS, but plagued with an authenticate, register, and vallidate process that irritated and aggrivates.  2K preceeds this, and yet is very similar to XP (once you revert XP to Classic view).  There are a few reasons or areas where XP is ahead, but only slightly.

The chief difference is in that a Bart PE burn of a boot CD having XP with SP2 on it is able to access and format a large hard drive.  
To do the same with 2K, it isn't enough to try the same thing with SP4 (which is applied belatedly), you have to burn a boot CD with something called USP 5.1, and while I could find Unauthorized Service Pack 5.1, nothing actuall explains how to create the boot CD with 2K and USP 5.1.

That put me in the position of not being able to pre-specify a client's VDI having 55 GB of space on it, as 2k cannot natively handle that much, so I reverted to XP with SP2 to circumvent this limit, then completely copied my True Image contents over it, which replaced XP with 2K.  Now if someone kobbles 2k together with USP 5.1, this step should prove unnecessary.

---

### Post by cariboo on 2009-09-02
Just to let you know Virtualbox will let you install almost any os. I have 3 linux distributions and 4 windows version installed. I used a mix of dvd's and iso's to install them. Use the pass through cd/dvd option to install from disk.

I'm running Karmic as my main os, for a while I could not burn cd's. To work around it I installed Jaunty in a vm and used it to burn cd's until Karmic was fixed.

---

### Post by oldefoxx on 2009-09-04
Of course you are right as to the fact that VirtualBox lets you set up multiple guest OSes, and they can be all the same or different versions of Windows, Linux Distros, whatever.  I even tried setting up versions of Windows 98 and MS DOS 6.22, and the installs seem to go okay, but using these 16-bit OSes seemed rather problematic.  I just decided that sticking with 32-bit versions of Windows was the better way to go.

Microsoft's insistence on validating XP and later versions of Windows does create an obsticle of sorts.  But if you note, almost all the fixes and patches that Microsoft releases are intended to reduce the OS's vulnerability to being hacked.  It hardly ever releases anything to expand the capability of the OS itself.  For such feature enrichments, you are expected to buy the next OS version when it becomes available.  You can go months before seeing a patch or fix for older versions of Windows.  With Ubuntu,  I am used to not only fixes, but all manner of enhancements on almost a weekly basis, all for free and handled by the Update Manager.  I estimate about 50 updates made per week, and all downloaded and applied at once.  How can you beat that kind of service and response?  You can alos submit your own bug reports with Ubuntu, be advised of any responses, and may eventually see your problem resolved.  Ever try to report a problem of any kind to Microsoft?

The more I use Ubuntu, the less willing I am to make allowances for Windows' shortcomings.  I tried to burn three copies of some folders to CD's last night using Nero, and after that attempt found nothing actually burned to the CDs.  No warning, no explanation, no idea why not.  I switched to Ubuntu and used a CD Creator program found under Acessories/Sound and Video, and tried again.  It even allowed me to control a box that allowed for better compatibility with Windows, burned the three CD, able to see the burn buffer progress, told of the burn rate and time remaining, and it went back and calculated a checksum that was burned to each CD as well.  Just to be sure, I went back under Windows and checked the contents of each CD, and the folders and files were all there.  How much of this was the fault of Nero, and how much is it's dependency on Windows services is unknown, but I'm to the point of reasoning that if a Window's Application fails to give good service, then part of that might lie with Windows itself.

I've come to the point of just telling everyone that the best way to go is Ubuntu as host, VirtualBox for your VM, and some 32-bit version of Windows as a guest under VirtualBox.  Then who cares if you pass Microsoft Genuine Vertification or not?  You may not get patches if it doesn't but the safeguards of having your Windows client surrounded by Ubuntu and VirtualBox means greater security anyway, like right away.  For most users, Windows leaves you vulnerable to attacks over the network until you are able to get the needed downloads all installed.  But that does not apply when Windows is set up as a client.  And if you want, yes, there is some protection software available for Ubuntu, but there is not the same need for it as Windows requires.

But let's say you feel shaky at this point.  There is also your spouse and kids to consider, or maybe someone else involved.  That is where the LiveCD of Ubuntu might persuade others that they would also like to see a change.  Or you can try one of the other possible combinations, maybe have Windows as host, VirtualBox as VM, and Ubuntu as client, or just install Ubuntu under Windows.  I am not as keen on these approaches, as you still have Windows in the dominant position, but others like this approach well enough.  

Ah, but then someone cries out, "Wait! Give Windows 7 a chance!"
What for?  And why bother?  You still are going to get stuck with upgrade costs and a relearning curve.  Maybe there is some job position out there that you might then qualify for, but in my book it would make more sence for many companies to embrace ways to keep using the resident version of Windows and applications rather than to reinvest in these, and have to deal with retraining programs as well.  They might have a high regard for your advanced awareness of how Windows can be superceeded or made a minor player as the company contemplates moving forward.
    
Just food for thought.

---

### Post by oldefoxx on 2009-09-16
I was caught by the fact that Microsoft seems to have dropped Windows 2000 support from its customary Windows Update process.  You try clicking on Express, Custom, or change to Microsoft Update, and you are taken to a dead end page that just gives you some links to click on for more information.  This change has been in effect for several days, so I guess it is the way things will be from now on.  According to my nephew, XP is still getting updated, but I guess that is just a matter of time now.

Not pleased, but not entirely unexpected.  If you can get up to SP4, you are in pretty good shape with Windows 2000, and one of the links will take you to where you can still register for post-SP4 hotfixes if and when they come out.  It's a different process though, and means you have to be more involved, even providing personal contact information like an email address.  I guess the idea is to make you see the wisdom of just doling out more money for the latest and greatest from Microsoft.

Better idea in my book is just move on to Ubuntu, and target any version of Windows as simply a client under a VM, your choice as to which.  Oh, I guess it's time to go, as the Ubuntu Update Manager is telling me i have a few more updates available and wants my permission to go ahead and install them.  That is at least twice this has happened this week.  Oh well, it's all free, so who am I to complain?

---

### Post by oldefoxx on 2009-09-20
The point I made concerning some of the weaknesses of Windows should have mentioned a new one, at least in my book.  Hook up a large drive under Windows 2000, and it takes forever for My Computer to come up and show you all attached drives.  That is because Windows 2000 is doing a directory scan per drive first, and stick in a CD or DVD that it has trouble accessing and you get the same results.

Of course you could make the counterpoint that Windows 2000 is an outmoded OS, but then compare those results with what happens when you check your drives under Linux.  Now that is speedy, and yet Linux is not what most people would consider leading edge among OSes.  But it does evolve, where Windows really does not, except to see new versions replace the old, but at some cost and loss of compatibility.

What might be interesting is to see someone install Windows 7 as a client under a VM like VirtualBox, then see what the results will be.  I expect that they will not be all that great, first because to get any enhanced functionality under a VM, you pretty much have to run the VBoxGuestAdditions, which is drivers and such that bring some of the outside hardware aspects down into the VM for the client to access and use.  In due course, with some added effort, a collection of software to aid Windows 7 run well as a client will get introduced, but a client is never going to be all that it would be if placed on its own in a hardware environment.  So my expectations in this regard are rather low for starters.

Some might look at multiple processors in PCs as the bridge that will give us the best array of multiple OSes working together.  It's a possibility I suppose, but not an expected one.  In the early days of mainframe development, the idea of linking several computers together that would somehow dominate the sceen just did not materialize.  We did not know how to write the system software that was needed, and we could not agree on the criteria involved, or determine beforehand what reactions computers should display when faced with either uncertainty or conflictive situations.  What we did instead was program the computers to be reactive to expected situations, and to take guidance from trained operators.  Thus, these supposedly dominant machines became mere servants, or what we refer to as severs.  The simple terminals or computer interfaces through which humans interconnect to these machines made us the clients, to which the servers were in service and responsive to.

Besides, it is not the interaction of the OSes that we crave, but the interchange between applications that we seek.  Made some applications redundant with others, we go with just the ones that best fit our needs or understanding.  Even if we looked for a time when a PC conld go peer-to-peer between multiple OSes, why would we hunger of all that redundancy in terms of the OS, applications, or even accumulations of data?  Will it make us smarter or more productive?  I don't think so.

The way I see it, a VM serves as a temporary bridge, carrying us from the old, known methods to a newer, hopefully more beneficial approach.  As a bridge, it lets us see how to span certain gaps, and may ease our way going forward, or at least allow us to prolong the inevitable.  Have you ever seen what happens to a business or enterprise that attempts to move forward without some suitable bridge in place?   They have to keep doing it the old way while groundwork is made for the new process, then run in parallel for a time until it can be judged that the two approaches can be rated against each other, then there has to be a shift from the old way to the new way.  But the problem is, that workers are still stuck in the old way and do not identify with the new way, and new workers are deemed a threat to the existing ones, and there is more than double the expense involved while all this is going on, with no significant gains made on either side.

With a PC and an installed VM, an attempt at parity between the two worlds is possible, and can be best mastered at the rate that each worker can achieve and maintain on their own.  Nobody is forced to cross until they feel ready to do so.  But once radical change is brought forward on the new side, a real issue comes forth:  Do you attempt the same thing with the old side, or do you now mandate that even the laggards must shift now?  In some cases, a restudy of the old methods has shown areas of simplification and enhancements that just meant placing the refinements there and forgetting the idea of moving forward to something entirely new as being the most effective solution.

Probably something worth thinking about.  With game players, it is not about anything other than being able to play their favorites, and so none of this likely applies to them in any case.  The lure for them is either keep playing what they have, or to be lured by the prospect of a better selection of games to choose from, possibly both attractions at the same time.

---

