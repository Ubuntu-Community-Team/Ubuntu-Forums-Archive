---
title: "how to update file-roller?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by hermitical on 2009-04-13
Hi

I want to update file-roller from 2.22.3 (I'm on Hardy and this is native) to 2.24.1. This is so I can create multi-part archives (zip or rar) for uploading. In 2.22.3 there is no 'other options' button which as I understand is where the option to create a multi-part archive is.

I tried uninstalling file-roller 2.22.3 through Synaptic but it said that it needed to uninstall ubuntu-desktop as well, I thought this wouldn't be a good idea!?

Any help appreciated

---

### Post by cariboo on 2009-04-13
Have a look [here]("http://packages.ubuntu.com/") for different versions of file-roller.

Jim

---

### Post by hermitical on 2009-04-13
thanks Jim, I have found different versions but what I'm not sure about is how to update it.

I've downloaded the .deb for 2.24.1. If I open that will it just override 2.22.3? Because as I said if I try to uninstall via Synaptic it tells me it will reomove ubuntu-desktop as well

---

### Post by cariboo on 2009-04-13
The newer version should overwrite the older version.

Gdebi will tell you that an older version is installed already. The only problem I can see, that if you try to install the version from the Jaunty repos, you amy not be able to because of needed python dependencies. There is a change to a newer version in Jaunty.

Jim

---

### Post by hermitical on 2009-04-13
many thanks Jim

---

### Post by hermitical on 2009-04-13
getting this message:

Error: Depencency is not satisfiable: libglib 2.0-0

---

### Post by hermitical on 2009-04-13
would that be related to something else I asked about?

> **hermitical said:**
> Hi folks, please be gentle!

trying to install gwibber from synaptic on Hardy. Getting following message

gwibber:
 Depends: libwebkit-1.0-1  but it is not installable
 Depends: python-webkitgtk but it is not going to be installed

anyone help or talk me through?

thanks...

---

### Post by Paqman on 2009-04-13
> **hermitical said:**
> getting this message:

Error: Depencency is not satisfiable: libglib 2.0-0

That's the problem cariboo907 mentioned you might hit. You'll need to find a .deb for that version of glib as well (and any other dependencies that file-roller has)

Might be easiest to hold off until Jaunty is released next week and then upgrade your system. Jaunty will have file-roller 2.26

---

### Post by hermitical on 2009-04-13
fair enough....cheers!

---

