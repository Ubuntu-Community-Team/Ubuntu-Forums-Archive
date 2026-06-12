---
title: "Adobe Reader source"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-03
Hi,
I am going to install Adobe Reader but I have no root access. Does anyone know where to get its source files from where I could build it? Thanks!

---

### Post by Roanoke on 2009-03-03
It isn't open source, and there is no way to install an application without root access.

---

### Post by lindsay7 on 2009-03-03
I just downloaded it last night from the Adobe web site.  Make sure you get the .deb file. You should get the adobe flash and adobe flash plugin-non free. I think I got the plug in from the Synatic program manager.

---

### Post by asmoore82 on 2009-03-03
> **Roanoke said:**
> It isn't open source, and there is no way to install an application without root access.

Ahh, with Linux there is always a way ...

1. Download the official Adobe Reader *.deb file
2. Open a Terminal and
```
dpkg-deb -X <official_acroread.deb> .local/
```
you can click and drag the *.deb file into the Terminal to spell it perfectly.
3. Right Click on the Desktop -> "Create Launcher"
4. Type "Adobe Reader 8" in the Name field
5. Click "Browse;" navigate to and pick "<your_home>/.local/opt/Adobe/Reader8/bin/acroread"
6. Click Launcher Icon on the left, Click "Browse" at the top;
navigate to and pick "<your_home>/.local/opt/Adobe/Reader8/Resource/Icons/48x48" and click "Open;"
pick AdobeReader8.png and click "OK"
7. Click "OK" in the "Create Launcher" dialog

This will install Adobe Reader for your user account only - no root access required.

Whew - I much prefer Evince to the Official Adobe Reader.

---

### Post by starcannon on 2009-03-03
> **asmoore82 said:**
> Ahh, with Linux there is always a way ...

1. Download the official Adobe Reader *.deb file
2. Open a Terminal and
```
dpkg-deb -X <official_acroread.deb> .local/
```you can click and drag the *.deb file into the Terminal to spell it perfectly.
3. Right Click on the Desktop -> "Create Launcher"
4. Type "Adobe Reader 8" in the Name field
5. Click "Browse;" navigate to and pick "<your_home>/.local/opt/Adobe/Reader8/bin/acroread"
6. Click Launcher Icon on the left, Click "Browse" at the top;
navigate to and pick "<your_home>/.local/opt/Adobe/Reader8/Resource/Icons/48x48" and click "Open;"
pick AdobeReader8.png and click "OK"
7. Click "OK" in the "Create Launcher" dialog

This will install Adobe Reader for your user account only - no root access required.

Whew - I much prefer Evince to the Official Adobe Reader.

Wow nice trick, thanks!

---

### Post by flylehe on 2009-03-03
Thanks!
Is this a general way to install many softwares without root?
Is it also similar for Ret Hat based Linux? I have to work on Centos in my office. :(

---

