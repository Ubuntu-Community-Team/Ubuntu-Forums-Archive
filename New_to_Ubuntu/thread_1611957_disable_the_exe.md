---
title: "disable the exe"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by thinkLinuX on 2010-11-02
is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.


Hi all how can i avoid this?
Any advise? Thank you

---

### Post by redbook4574 on 2010-11-02
My advise, don't avoid it.

If you trust the file simply right click on the exe file and in permissions tick the box "Allow executing file as a program".

---

### Post by Bölvaður on 2010-11-02
I will need more details here. I have no idea what this is about but Im willing to help when given enough information.

---

### Post by Rubi1200 on 2010-11-02
The security model in place on Ubuntu requires this:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required](https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required)

As Bölvaður already asked, what exactly are we talking about here?

A file you downloaded and cannot open?

A means of reducing the security mechanisms designed to protect your system?

---

### Post by ironic.demise on 2010-11-02
```
chmod +x path/to/file
```

---

### Post by mc4man on 2010-11-02
> how can i **avoid** this?
Many ways, here's some

Use wine to open any .exe instead of 'wine windows program loader' - a one time setup from r. click on any .exe -> open with -> other application - use a custom command
For command just use 
wine
In the future wine will be seen in the open with menu and can be made the default

Use wine from the team wine ppa (same maintainer as ubuntu) - they've removed the cautious-launcher crap
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

Edit the wine.desktop to remove the cautious launcher - just ask.

> security mechanisms designed to protect your system? 
As currently implemented has virtually no value - a bit of a joke actually

---

### Post by thinkLinuX on 2010-11-04
can i install autocad2011 in ubuntu?

---

### Post by TBABill on 2010-11-04
No, it is not a native Linux program and I doubt you would get the expected performance for such an intense program through Wine. From the website, here are the requirements:
 
[LIST]
[*]Microsoft Windows 7 Enterprise, Ultimate, Professional, or Home Premium ([compare Windows 7 versions]("http://www.microsoft.com/windows/windows-7/compare/default.aspx")); Microsoft Windows Vista Enterprise, Business, or Ultimate (SP1 or later) ([compare Windows Vista versions]("http://www.microsoft.com/windowsvista/versions")); or Microsoft Windows XP Professional (SP2 or later)
[*]AMD Athlon 64 with SSE2 technology, AMD Opteron® processor with SSE2 technology, Intel® Xeon® processor with Intel EM64T support and SSE2 technology, or Intel Pentium 4 with Intel EM64T support and SSE2 technology
[*]2 GB RAM
[*]2 GB free space for installation
[*]1,280 x 1,024 true color video display adapter 128 MB or greater, Microsoft® Direct3D®-capable workstation-class graphics card
[*]1,024 x 768 display resolution with true color
[*]Internet Explorer 7.0 or later
[*]Install from download or DVD
[/LIST]

---

### Post by thinkLinuX on 2010-11-04
Hmmm is there any software that can read and edit DWG cad drawing?

---

### Post by anewguy on 2010-11-04
Dumb question - have you checked qcad in synaptic package manager?  I needed a cad program at one time and it worked great.

Dave ;)

EDIT:  Never mind - qcad doesn't support dwg.  I've checked a little on the net for a dwg to dxf converter (qcad uses dxf) but so far haven't turned up much.

---

### Post by migs73 on 2010-11-04
> **anewguy said:**
> Dumb question - have you checked qcad in synaptic package manager?  I needed a cad program at one time and it worked great.

Dave ;)

EDIT:  Never mind - qcad doesn't support dwg.  I've checked a little on the net for a dwg to dxf converter (qcad uses dxf) but so far haven't turned up much.

It needs conversion from DWG as it doesn't open them natively. It uses DXF files.


EDIT: AAGHH Dave!!! Your edit beat my post!!

EDIT AGAIN: This is a linux converter for those files I believe, I've not tried it though;
    [http://lx-viewer.sourceforge.net/index.php](http://lx-viewer.sourceforge.net/index.php)

---

### Post by anewguy on 2010-11-04
lx-viewer is supposed to do it, but from what I read (maybe it's been updated??) it couldn't handle files from AutoCad 2005.  Apparently something different there and at least in what I read lx-viewer only handles(handled?) files through 2001.

I did see a non-free non-open-source one advertised for I believe $45.  From what I read, there's been a lot of talk on the subject.

Dave ;)

BTW - Migs73, where did you find your avatar?  I was forced (by a company that represents the copyright holder) to remove what I had been using.  Want to find something different but also must be free with no restrictions.

---

### Post by migs73 on 2010-11-04
> **anewguy said:**
> 

BTW - Migs73, where did you find your avatar?  I was forced (by a company that represents the copyright holder) to remove what I had been using.  Want to find something different but also must be free with no restrictions.
I am well aware of your FS/GL issues and have said before I miss your Amoeba!!

Tux came from;

[http://www.isc.tamu.edu/~lewing/linux/](http://www.isc.tamu.edu/~lewing/linux/) 
  
with a bit of GIMPing to put the saltire across his chest.

OP I think it could be possible (getting back to the thread), to have whoever sends you the DWG files to send them in DXF as AutoCAD (I think?) can save files in DXF.

---

### Post by anewguy on 2010-11-04
+1  - if autocad can save in dfx that would be something I'd try as well.

migs73:  thanks again for the sympathy on the avatar issue, and thanks for the link - I'll be looking there later tonight.


Dave ;)

---

