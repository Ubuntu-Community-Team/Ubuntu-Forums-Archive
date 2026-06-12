---
title: "How to print to Mac OS X attached usb printer"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by perchecreek on 2009-08-31
Does anyone know how to print from Ubuntu to a usb printer that is attached to an OS X Mac?  I am able to print from OS X to the OS X box (in fact, the same box, which dual boots OS X and Ubuntu).  Ubuntu's print setup dialog is ... unhelpful. It has been several years, and I've yet to get this to work.

---

### Post by Tclarkie on 2009-08-31
so, watt'a you wanna do

---

### Post by LowSky on 2009-08-31
on the Mac go o this website
 [http://localhost:631](http://localhost:631)
if it doenst work the address also has it for download
[http://www.cups.org/index.php](http://www.cups.org/index.php)

its called CUPS, built by apple and usable on any *nix based computer.
set up your printer from there to be shared, instructions are found here, [http://www.cups.org/index.php](http://www.cups.org/index.php)


now log onto the ubutn PC use firefox to access  [http://localhost:631](http://localhost:631)
make sure hte printer can be seen if not add yourself as a user, and you should be set

---

### Post by perchecreek on 2009-08-31
Let me ammend my request: I need coherent, end user oriented instructions for how to set up access from Ubuntu Jaunty/9.04 to an OS X box that has a usb printer attached.  Referrals to cups.org, google, or Ubuntu's help facilities will not suffice -- I have checked in these places, and it is taking too long to make this work: instructions are not clear, complete or germaine.  

Instructions should give step-by-step; context or previous knowledge should never be assumed.  For example, "Start from the desktop in Ubuntu. Click on menu item System, Preferences, Printer Setup.  Click on the 'New' printer icon. Choose radio button / check box / Click on menu item ... " etc. No instruction should be given that is not visible in the current dialog (do not assume that the user knows what you're talking about!).

Or, conversely, if it is not possible to easily configure printing to OS X based printers from Ubuntu, just say so.  

Apologies in advance, but this (printing) works in OS X (and by "work," I mean an ordinary end user can configure a printer on a LAN quickly and with little help), but is inscrutable (at least to me) in Ubuntu.

---

### Post by fela on 2009-08-31
> **perchecreek said:**
> Let me ammend my request: I need coherent, end user oriented instructions for how to set up access from Ubuntu Jaunty/9.04 to an OS X box that has a usb printer attached.  Referrals to cups.org, google, or Ubuntu's help facilities will not suffice -- I have checked in these places, and it is taking too long to make this work: instructions are not clear, complete or germaine.  

Instructions should give step-by-step; context or previous knowledge should never be assumed.  For example, "Start from the desktop in Ubuntu. Click on menu item System, Preferences, Printer Setup.  Click on the 'New' printer icon. Choose radio button / check box / Click on menu item ... " etc. No instruction should be given that is not visible in the current dialog (do not assume that the user knows what you're talking about!).

Or, conversely, if it is not possible to easily configure printing to OS X based printers from Ubuntu, just say so.  

Apologies in advance, but this (printing) works in OS X (and by "work," I mean an ordinary end user can configure a printer on a LAN quickly and with little help), but is inscrutable (at least to me) in Ubuntu.

Apologies to you, but with an OS that isn't made by a single entity and with no prior knowledge as to your setup, we can't help you in such a basic step-by-step manner, due to the existence of too many variables. Maybe if you want to carry on using Linux you should think about using your own initiative just a bit and learning how to fix your problems with the great guidance that the volunteers here give you.

Secondly, you cannot demand support here as 1) you don't pay for it and 2) it is obnoxious even if you did pay for it.

Have a nice day and I hope you get your printer working, just try and use your own initiative instead of depending solely on the guesswork of others.

---

### Post by perchecreek on 2009-08-31
Chiding end users when they ask for help is, well, not helpful.  It certainly wouldn't work on any help desk I've ever been around -- it would get you fired.  I didn't ask for an evaluation of my character, I asked for written instructions of a generic sort.  

I did leave out that the OS X versions, on both boxes, was 10.4.11.

Again, the goal is to create (or find) instructions for setting up printing from Jaunty 9.04 to an OS X usb printer (see above).

Sadly, my time is about up for finding a resolution to this problem.  

TIA.

---

### Post by fela on 2009-09-01
> **perchecreek said:**
> Chiding end users when they ask for help is, well, not helpful.  It certainly wouldn't work on any help desk I've ever been around -- it would get you fired.  I didn't ask for an evaluation of my character, I asked for written instructions of a generic sort.

And that's how paid help desks work. This is not a help desk, it is a forum, where people give support out of the kindness of their hearts, not as a job. You just cannot demand support here, you ask for it and if it doesn't get served to you on a plate then you have to give it a bit of effort on your part.

> I did leave out that the OS X versions, on both boxes, was 10.4.11.

Again, the goal is to create (or find) instructions for setting up printing from Jaunty 9.04 to an OS X usb printer (see above).

Sadly, my time is about up for finding a resolution to this problem.  

TIA.

I think you should find a resolution to your problem, and if you're really nice you could put up a HOWTO on these forums showing others how you resolved the problem.

I'm sorry but I don't really have enough information right now to help fix your problem.

What exactly happens when you try adding the printer on ubuntu? Does it automatically find the printer that's attached to the (up and running) mac print server? If not, first I'd make sure that you can ping the mac server. If the IP address of the mac server is 192.168.1.3 for example, you'd run this on the linux box:

```
ping 192.168.1.3
```

If it says things like 'XX bytes from 192.168.1.3' etc (or something similar) then it's fine and you can ping it alright.

As I said you haven't really given enough helpful info so we can sort the problem out. I was pointing out your obnoxious behaviour so we could be more constructive and have a more civilized chat about what the problem is and how to resolve it. I didn't mean to offend you or anything.

---

### Post by LowSky on 2009-09-01
how hard is it to use google, sorry I'm mad when people post that we dont give perfect answers, and berate us on how poor we are at tech support, I'm think I'm being nice giving free advice and such and this guy thinks I'm treating him like crap.... welll then here ya go, enjoy
[Click here]("http://lmgtfy.com/?q=mac+osx+%20share+printer+with+linux")
Follow the first link it brings up

see if your printer is compatible with Linux
[http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi)


next time tell us how child-like you are, and that you need coddled, this way I know to ask all the dumb questions, like What version of OS/X, what Version of Ubuntu, how are they networked together, what kind of printer, do you have the Linux drivers for said printer, ETC...

If you want help, please give all the infomation you can, dont be stingy... How fun is it to try to help only to find out you are using some out of date operating system or a printer that wont work at all with Linux

---

### Post by fela on 2009-09-02
+1 to lowsky

and to the OP, yeah stop whining if you want free tech support.

---

### Post by 3rdalbum on 2009-09-02
> **perchecreek said:**
> Apologies in advance, but this (printing) works in OS X (and by "work," I mean an ordinary end user can configure a printer on a LAN quickly and with little help), but is inscrutable (at least to me) in Ubuntu.

It doesn't surprise me if OS X-to-OS X printing works easily. Ubuntu-to-Ubuntu printing works easily too.

You might struggle to find people here who have OS X experience, but you'd generally get advice about "On the OS X machine, access the CUPS interface and turn on printer sharing. On the Ubuntu machine, go to the Printers panel, go to the File menu and Add New Printer. The shared printer should be detected."

Apple likes using its Bonjour/Zero-Conf protocol for doing network-y things, but CUPS itself doesn't need this Apple nonsense to share printers easily. You just need to turn on the feature in CUPS.

---

### Post by fela on 2009-09-02
Plus, if the problem might be down to Mac OSX why are you blaming Ubuntu? If Ubuntu was running the print server and OSX was the client, would you blame OSX instead? I doubt it somehow.

Have you even seen how easy it is getting printing working with both the client and server running Ubuntu?

You could just as easily say that OSX is the issue here, as you could say Ubuntu is. Ubuntu being the print server has nothing to do with it; client problems are just as bad as server problems. For instance, I have a problem where I can only print from Linux/UNIX clients to my Linux print server, windows doesn't seem to be able to print to it. Would you say this is a *nix issue or a windows issue?

---

### Post by jrothwell97 on 2009-09-02
The problem is with neither OS X or Ubuntu, as both use the same printing subsystem, CUPS.

In System Preferences on the Mac, open the Sharing panel and enable printer sharing if it hasn't already been found. Now find out the IP address of your Mac. You can do this on the Network pane of System Preferences by selecting the connection to the network and clicking "Configure", then choosing the TCP/IP tab. (See [the attached screenshot](http://ubuntuforums.org/attachment.php?attachmentid=127155&stc=1&d=1251891861) if you're lost.)

Instructions for connecting your Ubuntu client are available [on this web site](http://blog.delgurth.com/2009/01/06/connecting-ubuntu-client-to-cups-server/) - this is stupidly complex for such a trivial task, I know, but unfortunately there's no GUI to do it yet, at least not that I'm aware of. The line should look something like

```
MacPrintServer mac.ip.goes.here
```

If this fails, reply here and we'll try connecting using SMB instead of CUPS.

And now, a rant.

To the OP: this isn't a paid help desk, and people *do* come here and spend their time of their own volition to try and help people. Patience is required on both sides. However, I can understand why you feel bewildered and annoyed. Just don't whine in future, or you'll likely be slapped with an image macro or told to JFGI/RTFM.

And to everyone else: this thread was posted in the Absolute Beginner Talk forum. In my opinion, the process for connecting to the CUPS server is far too convoluted already (in this case, it *is* Ubuntu's problem), but creating an additional user on the server is completely irrelevant. It mystifies me as to how a beginner is supposed to understand

> now log onto the ubutn PC use firefox to access [http://localhost:631](http://localhost:631)
make sure hte printer can be seen if not add yourself as a user, and you should be set 

which are incorrect anyway: *if* the user needed to create a new user on the server, he'd go to [http://his.mac.ip.address:631](http://his.mac.ip.address:631), not localhost.

Also, that last post by Fela, which is, indirectly, accusing the OP of being a Macintard, is completely inappropriate. In this case, the problem has *nothing* to do with OS X. At all. So blaming it on the shortcomings of Ubuntu is, at least partly, correct.

---

### Post by fela on 2009-09-02
> **jrothwell97 said:**
> Also, that last post by Fela, which is, indirectly, accusing the OP of being a Macintard, is completely inappropriate. In this case, the problem has *nothing* to do with OS X. At all. So blaming it on the shortcomings of Ubuntu is, at least partly, correct.

Didn't I say it **might** be due to OSX? I didn't know for sure, and I thought it might have been OSX. So I said that.

And don't go round accusing me of accusing people of being a *macintard*, whatever that's supposed to be. It's dumb and immature.

And also: this problem is nothing to do with the shortcomings of Ubuntu, yes I agree ubuntu has LOTS of shortcomings, but this isn't one of them. Linux is not windows or OSX, things are configured using text files in Linux and there isn't a GUI for everything, that's just the way it is. It isn't a shortcoming, it's just one way of using a computer.

---

### Post by perchecreek on 2009-09-05
Given the churlish tone of some of the replies I received, I thought it appropriate to provide a reference to Jamie Zawinski's general statement about <a href="http://www.jwz.org/doc/linux.html">Linux and its more zealous adherents</a>.

Zawinski stated: 

<blockquote> See, unlike most hackers, I get little joy out of figuring out how to install the latest toy. I don't get much sense of reward from having discovered how to get the Foo card to coexist with the Bar card. As far as I'm concerned, that crap is a solved problem, and not worth revisiting. That's like banging rocks together and being proud that you've re-derived fire from first principles. It's boring.</blockquote>

And:

<blockquote>This is the part where I start getting hate mail from people, and cheerleading messages telling me to take a look at it again, because it's so much better now. I understand. I'll take your word for it. And when the time comes to replace the O2 I have today, maybe my next machine will run Linux. But as we all know, Linux is only free if your time has no value, and I find that my time is better spent doing things other than the endless moving-target-upgrade dance.</blockquote>

We've come a long way, and most of the hardware compatibility problems Zawinski refers to have been resolved, and many of the major distributions and desktop environments have arrived at a point where they're 98% as good as Windows and OS X.  (Or even better, as is my opinion, save for failings in a few areas.) 

Unfortunately, a critical failure of just one component -- such as in printer discovery, interoperability, and interface design -- is enough to stop inexperienced users dead in their tracks.  Who is responsible is not really relevant (Samba or Cups or Apple or Ubuntu or Gnome or KDE or Linux or Adobe or HP or Epson or the ISO or Vint Cerf or ...


Thanks to those who did offer assistance without recrimination.

---

### Post by fela on 2009-09-06
@perchecreek: No, the one with the bad tone and rudeness was you.

The fact that configuring hardware and software to work with each other takes time, effort and practice, will always remain a fact unless one company takes over everything which isn't gonna happen (and shouldn't).

If you decide to use an operating system built from the ground up by the community and designed with the users' choices in mind, you can't complain when you have to spend a bit of time getting things to work. Of course I think it's great if you use Linux, but if you want tech support in the format that you ask (demand) for, you shouldn't use Linux, because Linux tech support is in the format of the community helping the community, not the company helping the community, and for that reason it's not gonna be perfect and it's not gonna treat you like the customer (as in the customer is always right), because you're not a customer.

---

### Post by perchecreek on 2009-12-07
This worked (how to setup print to an OS X 10.4.1 Tiger usb hosted printer Epson Stylus CX4200 from Ubuntu 9.04 Jaunty Jackalope):

> 

[URL="http://ubuntuforums.org/showthread.php?t=56940"]
Printing to a Mac OSX CUPS Printer[/URL]

bozaman
August 14th, 2005, 04:35 PM
Having just spent a substantial portion of my day attempting to get printing set up on my Ubuntu (Hoary) Intel-based laptop in order to print to a Mac OSX (10.4.2) hosted USB printer (Samsung ML-1450), I thought I would share the steps involved for others to have at their disposal...

1. Set-up your printer and verify that it works correctly in Mac OSX.
2. Enable printer sharing in the Mac OSX System Preferences panel.
3. Verify the Mac OSX printer queue name:
- Open Terminal
- Type: "view /etc/printcap" (without the quotes), press enter
- Find your printer in the list (if you only have one printer this should be easy)
- The value before the "|" is your Mac OSX printer queue name ("ML_1450", for example, is the Mac OSX printer queue name for my situation)
4. Within Ubuntu, go to System, Administration, Printing
5. Go to Printer, Add Printer
6. Printer Type: Network Printer, CUPS Printer (IPP)
7. URI:
- http://<IP address of Mac OSX>:631/printers/<Mac OSX printer queue name> (If you have set up your /etc/hosts file with a valid IP and host name for your Mac OSX system, then you can substitue the host name for the IP address in the URI)
8. Printer Driver:
- Manufacturer: Raw
- Model: Queue
- Driver: Standard
9. Apply

This should create a new printer for you to access. Right click, select "Properties" and set the correct Paper and Advanced settings for your situation and then "Print a Test Page". If all went well, you should have a test print appear in a few minutes.

I relied upon a lot of trial and error, the Ubuntu forums and the Printer Sharing from OSX ([http://members.cox.net/18james/osx_printer_sharing.html](http://members.cox.net/18james/osx_printer_sharing.html)) web site supported by Ronald Florence to get this set up and working for my situation. YMMV, but good luck!

Some subtle differences in syntax I experienced:

After bozamnan's step 4 (see quote, above), this happened:

A dialog window titled 'Printer configuration - localhost' opens.

Beginning at bozaman's step 5, I did this: Click on menu item 'Server', from drop down menu choose 'New', 'Printer' (there was no Printer, Add Printer menu choice). A dialog titled 'Please wait...' opens, then is replaced by a dialog titled 'New Printer' (apparently no printers were found on local subnet).  

Beneath text "Select Device" is a text box.  Click on triangle to left of text "Network Printer". Click on text "Internet Printing Protocol (ipp)".   Text to the right should change to "IPP Printer". Fill in text fields titled "Host:" and "Queue" using instructions given by bozaman.

A note:  There is also an icon that appears to mean "Create New Printer" (the icon is a piece of paper with a yellow star on its right corner). To the right of the icon is a downward pointing arrow, which, when clicked, drops a menu that has "Printer" and "Class" choices. Clicking on the "Printer" menu item opens the same dialog box that choosing Server, New, Printer opens (one titled "Please wait...", then another titled "New Printer").  I did not verify that this works, but the dialogs opened appear to be identical.  

Why doesn't the "Printer configuration - localhost" dialog have a choice 'Printer, New Printer'?  It's a mystery...

---

### Post by perchecreek on 2010-07-17
<blockquote>
Here is our first intimation of trouble. If I were Aunt Tillie the archetypal nontechnical user, I am at this point thinking "What in the holy fleeping frack does that mean? And just as importantly, why do I have to answer this question?" I do not, after all, have any Windows machines on my network. Nor any Netware boxes. And I certainly don't have a "Networked JetDirect", whatever that might be.

If the designers were half-smart about UI issues (like, say, Windows programmers) they'd probe the local network neighborhood and omit the impossible entries. If they were really smart (like, say, Mac programmers) they'd leave the impossible choices in but gray them out, signifying that if your system were configured a bit differently you really could print on a Windows machine, assuming you were unfortunate enough to own one.
</blockquote>

<a href://"http://www.catb.org/~esr/writings/cups-horror.html">The Luxury of Ignorance: An Open-Source Horror Story</a>, Eric S, Raymond

---

