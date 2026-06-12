---
title: "MadWifi Make problems"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by Nirevus on 2008-01-01
I'm trying to install MadWifi on an Acer Extensa 4220, to support the inbuilt wireless adapter. I've downloaded the madwifi source, and the fixes (although I'm not sure if the fixes are still required in Gutsy, the article hasn't been updated since Dapper.)

I get the following errors when trying to make.

```

Checking requirements... ok.
Checking kernel configuration... /bin/sh: Syntax error: "|" unexpected
make: *** [configcheck] Error 2

```

---

### Post by Nirevus on 2008-01-04
Anyone have any idea what might be causing this?

---

### Post by spd106 on 2008-01-04
Which article are you following?

Make sure you have the *build-essential* and the appropriate *linux-headers* packages installed.

---

### Post by Nirevus on 2008-01-05
I'm following [network manager MadWifi]("https://help.ubuntu.com/community/WifiDocs/NetworkManagerMadWifi") on the wiki.

Installed build-essential, and the error changes very slightly from:

```
Checking requirements... ok.
Checking kernel configuration... /bin/sh: Syntax error: "|" unexpected
make: *** [configcheck] Error 2
```#

To

```
Checking requirements... ok.
Checking kernel configuration... /bin/sh: Syntax error: "||" unexpected
make: *** [configcheck] Error 2
```

Notice the double pipe.

---

### Post by spd106 on 2008-01-07
That's a very old tutorial. I wouldn't bother with it as Ubuntu has included madwifi-ng since version 6.10. 

If your card doesn't work out of the box then you'll probably have more luck with ndiswrapper or maybe try the latest Madwifi from the project's svn repository.

[http://madwifi.org/wiki/UserDocs/](http://madwifi.org/wiki/UserDocs/)

---

### Post by mfeif on 2008-01-16
```
Checking requirements... ok.
Checking kernel configuration... /bin/sh: Syntax error: "|" unexpected
make: *** [configcheck] Error 2
```

I have the same problem; build-essential is installed, as are relevant source/header packages.

I can't use the included ubuntu madwifi as I'm on the *-server kernel, which doesn't include madwifi.

---

### Post by mfeif on 2008-01-16
I had some luck removing other kernels than server, and moving the madwifi svn source to /usr/src/ and making from there.

FYI.

---

