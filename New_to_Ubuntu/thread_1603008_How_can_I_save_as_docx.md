---
title: "How can I save as docx?"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Struggling1 on 2010-10-22
I use Ubuntu 8.04 and am trying to upgrade to 10.04.  When the update is run, the following message appears:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'skype-common' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.


Can someone help me?  The main reason I need to upgrade is that I **absolutely** need to be able to save documents as docx in order to send them on to someone else (work related, and it's non-negotiable).  Please can someone tell me how to upgrade and how to make Open Office save as docx.  
Please, with a cherry on top...

---

### Post by Paqman on 2010-10-22
This sounds like the problem:

> **Struggling1 said:**
> 
 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
** * Unofficial software packages not provided by Ubuntu**


Uninstall Skype and try again. You can always re-install Skype afterwards.

---

### Post by KeLa on 2010-10-22
Saving document in docx format is simple.
From "File" menu select "Save as" and click "+" next to "File type" to open list of file types and scroll down for "Microsoft Word 2007 XML" (docx) and thats it.

---

### Post by coffeecat on 2010-10-22
> **KeLa said:**
> Saving document in docx format is simple.
From "File" menu select "Save as" and click "+" next to "File type" to open list of file types and scroll down for "Microsoft Word 2007 XML" (docx) and thats it.

The way I read the OP is that they are currently using Ubuntu 8.04 which comes with a version of OO that does not support docx (iirc). That is why they want to upgrade to 10.04 - see their last paragraph.

---

### Post by sikander3786 on 2010-10-22
Before upgrading, make sure to disable all the custom repositories, ppa's from System > Administration > Software Sources as they can create problems at times.

---

### Post by Mark Phelps on 2010-10-22
Also, if you're running an ATI proprietary driver in 8.04, unless you have one of the newer HD 3x/4x/5x cards, that driver will NOT work in newer Ubuntu versions.  In that case, remove it before attempting the upgrade.

---

### Post by jmszr on 2010-10-22
Struggling1,

Because your immediate concern is saving documents in docx you could just upgrade your OpenOffice to 3.2 using this PPA: [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) . I have 3.2.0 installed in 8.04 and it will save in docx.

Then you can upgrade to 10.04 at your leisure.

---

### Post by ivarn on 2010-10-22
The 8.04 support ends in less then a year so you really should upgrade it anyway.
But yea, you dont have to upgrade the whole OS Just to get the latest version of a program.

---

### Post by Struggling1 on 2010-10-26
I do wish I'd waited for all the replies to come in before choosing a course of action.  Merely upgrading Open Office probably would have been best.  I removed Skype as advised on here, and then I proceeded to upgrade.  Everything was going fine until the computer screen went black, and it wouldn't respond to the mouse.  I left it for an hour or two.  Still black, so in my cleverness I decided to restart it manually (on off button).  Doom.  The computer is now in a zombie like state.  When I switch it on, it goes all DOS on me.  After pressing ESC and choosing something that said "Recovery Mode," I found I could eventually log in.  But the sound had gone; my USB stick isn't read; Evolution Mail won't open,and the absolute clincher (if you can call something so depressing that)is that it tells me it can't detect my modem.  No internet at home is akin to being placed on a time machine bound for the dark ages. Oh, there's more.  The terminal no longer works.  An error message about a child process (whatever that is) comes on.  I can still open and edit my documents, but without any drives working and no internet connection, there's no point since I can't "get anything out."  I even managed to somehow find something called root (which acts like the terminal window) when I was busy pressing ESC or F2 on booting (I forget which one), and typing in "pppoeconf" yields nothing - just a message about no ethernet card found or something.  So I am down to internet cafes etc etc, and hence my not replying to all those who'd sent through ideas.  I'm sure that the problem would be solvable for someone who knows about these things; it's just hard to believe that a computer that can boot up, albeit by hook and crook, could really be fit for a rubbish heap.  All the same, I am not computer savvy enough to sort this out on my own, so I reckon I should just buy another computer.  I mean, the CD drive won't read anything (hadn't for a while; think I once asked about that on here) so there's no way starting from scratch would work.  It's a disaster for me and a tough lesson learnt! :(

---

### Post by coffeecat on 2010-10-26
> **Struggling1 said:**
> I am not computer savvy enough to sort this out on my own, so I reckon I should just buy another computer.  I mean, the CD drive won't read anything (hadn't for a while; think I once asked about that on here) so there's no way starting from scratch would work.  It's a disaster for me and a tough lesson learnt! :(

Is that a desktop or a laptop? If a desktop, buying a replacement optical drive would be cheaper than buying a new computer. Far cheaper. Here in the UK I could buy one brand-new CD/DVD rewriter for the cost of a decent takeaway curry for two. Then you could boot up with a live CD of 10.04 or 10.10, test your hardware for compatibility, rescue any personal files that are on the internal HD and do a fresh installation.

---

### Post by Struggling1 on 2010-10-26
It's a laptop.  Acer 3680.  I'm in Germany and the cheapest laptops I've seen are about €300 give or take, and these are those little dinky things that look like toys.  It just seems like a rip off to me considering all the things you could do with 300 bucks.  You have to fork out at least 400 for something that is truly recognisable as a laptop.  I should probably try to find someone here who can have a look at my laptop just in case because, as I say, it does spew out messages on those DOS screens, but these mean nothing to me as I do not know what an X-server client is. :confused: This level of ignorance would be laughable if it weren't so stressful not having a computer at home.  Alas! :(

---

### Post by theozzlives on 2010-10-26
Try to go to the CLI (what you call DOS prompt) and try typing the following:
```
sudo dpkg --configure -a
sudo apt-get install -f
```
You can also boot recovery mode and instead of root prompt, choose fix broken packages.

---

### Post by coffeecat on 2010-10-26
Theoretically, it would be possible to repair the system, but since you did a hardware reset while it was doing a dist-upgrade the damage could be severe. It would be simpler and probably quicker to do a re-install.

I have another thought. Since the CD drive is non-functional and since replacing it would be more expensive than replacing an optical drive on a desktop (but still do-able) do you know if the BIOS will let you boot from USB? How old is the machine?

If you can boot from USB, then you could create a bootable pendrive from a desktop ISO and rescue your files and re-install using that. You'd need access to another machine to prepare the pendrive, of course.

By the way, those 'dinky' toys are probably netbooks. OK for what they are, but limiting. As far as laptops are concerned I myself would avoid anything at the lower end of the price range simply to avoid poor hardware. Which means that here in the UK, I wouldn't spend less than £500, or £450 with a special offer. I'll let you convert that into Euros.

---

### Post by Paddy Landau on 2010-10-26
Two things.

One:

To the best of my knowledge, Open Office can *read* .docx, but cannot *save as* .docx. It can save as .doc, but not as .docx. Not even the latest package. Sorry.

If using .docx (as opposed to .doc) is non-negotiable, then until Open  Office provides "save as" for .docx, you'll have to purchase a computer  with both Windows and Word.

(If anyone knows otherwise, please let me know!)

Two:

You'll probably be best off reinstalling Ubuntu 10.04 from scratch. *You did make a backup first, didn't you?*

If you haven't made a backup, you'd need to boot from a Live CD, find your data, back it up onto a USB disk or wherever, then reinstall. (If you have your /home directory on a separate partition, then you won't have to back up, but I'd recommend a backup anyway.)

---

### Post by Struggling1 on 2010-10-26
> **theozzlives said:**
> Try to go to the CLI (what you call DOS prompt) and try typing the following:
```
sudo dpkg --configure -a
sudo apt-get install -f
```
You can also boot recovery mode and instead of root prompt, choose fix broken packages.

OK, I will try this at home :-)

---

### Post by coffeecat on 2010-10-26
> **Paddy Landau said:**
> (If anyone knows otherwise, please let me know!

You're on! :p

In Open Office 3.2.1 at least you can save as docx. I thought the same as you until the other day when someone pulled me up for the same. It's easily missed though. In the file type drop down in the save window, docx is not grouped with the other MS filetypes. It's well down the list.

Read for docx was introduced in OO 3.0, but I don't know whether write is supported pre 3.2 or not.

---

### Post by KeLa on 2010-10-26
When out company upgraded to ms office 2007 and all started to save word, excel and powerpoint docs to *x format (xml format) and i had old 2003 version i had to use OpenOffice to open and edit those docs.

Second thing. About laptop and broken cd/dvd drive.
I had once laptop that i had to install ubuntu and laptop had broken cd player so i take
one working cd/dvd drive for desktop and one working 3.5 inch usb external hard drive
and replaced hard drive with the cd/dvd drive and booted from there. Worked like a charm and didn't cost anything because all needed parts found from home.

---

### Post by ezsit on 2010-10-26
If you are thinking seriously about buying a new computer, don't do anything to the old computer, don't touch the hard drive or try to repair it. If you get a new computer, remove the hard drive from the laptop and get a SATA - USB converter and plug the old hard drive in externally to the new computer to rescue the files and any other data you may have. If you attempt to repair or reinstall on the old hard drive, you may accidentally destroy any chance of recovering your files.

---

### Post by coffeecat on 2010-10-26
> **ezsit said:**
>  get a SATA - USB converter

The OP has a Acer 3680.  That was first released around the time you joined the forum. It's more than likely the internal drive is a PATA.

---

### Post by KeLa on 2010-10-26
> **coffeecat said:**
> The OP has a Acer 3680.  That was first released around the time you joined the forum. It's more than likely the internal drive is a PATA.

Actually it's no big problem because one adapter i got can handle desktop and laptop PATA drives as well as SATA drives and i think that kind of adapter is easier to find and it won't cost much
eg in [Amazon]("http://www.amazon.com/Drive-Adapter-Converter-Optical-External/dp/B002OV1VJW") it's $6.99

---

### Post by beew on 2010-10-26
> **Struggling1 said:**
> I use Ubuntu 8.04 and am trying to upgrade to 10.04.  When the update is run, the following message appears:


Can someone help me?  The main reason I need to upgrade is that I **absolutely** need to be able to save documents as docx in order to send them on to someone else (work related, and it's non-negotiable).  Please can someone tell me how to upgrade and how to make Open Office save as docx.  
Please, with a cherry on top...

It may be too late now but if all you wanted was to get an updated version of openoffice you could have just added this ppa to your sources list and then installed OO.O3.2 from Synaptic (Though personally I think an OS upgrade is long overdue, but I would have made a clean install instead)

[URL="https://launchpad.net/%7Eopenoffice-pkgs/+archive/ppa?field.series_filter=hardy"]https://launchpad.net/~openoffice-pkgs/+archive/ppa?field.series_filter=hardy
[/URL]

---

### Post by beew on 2010-10-26
> **Paddy Landau said:**
> Two things.

One:

To the best of my knowledge, Open Office can *read* .docx, but cannot *save as* .docx. It can save as .doc, but not as .docx. Not even the latest package. Sorry.



Yes you can. I just did, with embedded diagrams formulas and all, it renders flawlessly.

---

### Post by Paddy Landau on 2010-10-27
> **coffeecat said:**
> In Open Office 3.2.1 at least you can save as docx. ... In the file type drop down in the save window, docx is not grouped with the other MS filetypes. It's well down the list.
> **beew said:**
> Yes you can. I just did, with embedded diagrams formulas and all, it renders flawlessly.
Unfortunately, I don't see it! :(

I've attached a screen-shot of the "Save As" options that I get. Maybe I'm missing it, or perhaps I'm just a bit confused?

---

### Post by TeoBigusGeekus on 2010-10-27
Openoffice 3.2.0

---

### Post by Paddy Landau on 2010-10-27
> **TeoBigusGeekus said:**
> Openoffice 3.2.0
Huh! I don't have that option. I also don't have "OpenDocument Text (Flat XML)". I use Open Office 3.2.1, which is the latest version.

Are you using an extension, perhaps? Or did 3.2.0 have it, and 3.2.1 withdrew support?

---

### Post by TeoBigusGeekus on 2010-10-27
> **Paddy Landau said:**
> Huh! I don't have that option. I also don't have "OpenDocument Text (Flat XML)". I use Open Office 3.2.1, which is the latest version.

Are you using an extension, perhaps? Or did 3.2.0 have it, and 3.2.1 withdrew support?
No, nothing, just a standard lucid installation at work. I'll check with arch when at home and post back.

---

### Post by Paddy Landau on 2010-10-27
> **TeoBigusGeekus said:**
> No, nothing, just a standard lucid installation at work. I'll check with arch when at home and post back.
I've just spotted an [old Brainstorm]("http://brainstorm.ubuntu.com/idea/8129/"), which has been implemented. I suspect that this is implemented in the Ubuntu version of OO but not in the standard.

I uninstalled the Ubuntu version because of problems I had with OO and installed the standard version, so maybe that's why I don't have it.

If I'm right, then Ubuntu has an extra feature that the standard OO doesn't have. Oh well.

---

### Post by TeoBigusGeekus on 2010-10-27
> **Paddy Landau said:**
> I've just spotted an [old Brainstorm]("http://brainstorm.ubuntu.com/idea/8129/"), which has been implemented. I suspect that this is implemented in the Ubuntu version of OO but not in the standard.

I uninstalled the Ubuntu version because of problems I had with OO and installed the standard version, so maybe that's why I don't have it.

If I'm right, then Ubuntu has an extra feature that the standard OO doesn't have. Oh well.
No: Openoffice 3.2.1 on Arch

---

### Post by Paddy Landau on 2010-10-27
> **TeoBigusGeekus said:**
> No: Openoffice 3.2.1 on Arch
Ouch. I wonder why I've missed out?

I'll wait for OO 3.3.0 to come out. Or, over the weekend, I'll reinstall OO.

---

### Post by coffeecat on 2010-10-27
> **Paddy Landau said:**
> I uninstalled the Ubuntu version because of problems I had with OO and installed the standard version, so maybe that's why I don't have it.

If I'm right, then Ubuntu has an extra feature that the standard OO doesn't have. Oh well.

Despite the Oracle branding, Ubuntu uses the Novell Go-OO version so I wonder if docx save has been implemented in Go-OO but not in vanilla OO. Whatever...

> **Paddy Landau said:**
> I'll wait for OO 3.3.0 to come out.

With the way that Oracle seems intent on alienating the OO community and everyone involved, you may have a long wait. I believe Ubuntu will be using Libre Office in future versions - once it has been stabilised.

---

### Post by Paddy Landau on 2010-10-27
> **coffeecat said:**
> Despite the Oracle branding, Ubuntu uses the Novell Go-OO version so I wonder if docx save has been implemented in Go-OO but not in vanilla OO. Whatever...
Googling this, it appears that you're right. Apparently, docx from both Novell and OxygenOffice ([see OO post]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=20644#p93723")).

> **coffeecat said:**
> With the way that Oracle seems intent on alienating the OO community and everyone involved, you may have a long wait. I believe Ubuntu will be using Libre Office in future versions - once it has been stabilised.
I didn't realise Oracle was doing that. But according to the [newsletter 213]("http://ubuntuforums.org/showthread.php?t=1595749"), you're right about Ubuntu and LibreOffice. I still don't know why Oracle wanted to purchase Open Office; what's the business plan? [Open Office files Oracle divorce papers]("http://www.theregister.co.uk/2010/09/28/openoffice_independence_from_oracle/") (released today).

---

### Post by KeLa on 2010-10-27
> **Paddy Landau said:**
>  I still don't know why Oracle wanted to purchase Open Office

OpenOffice was part of Sun Microsystems that Oracle buy.

---

