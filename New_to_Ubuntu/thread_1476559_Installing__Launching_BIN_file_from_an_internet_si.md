---
title: "Installing / Launching BIN file from an internet site."
date: 2010-05-07
forum: New to Ubuntu
---

### Post by McRat on 2010-05-07
I downloaded GoogleEarthLinux.bin (world map app).  I am using 10.04 64bit with Gnome GUI.

When I double click, or right click and open, it says I need to associate it with an application.

Is there an installer app or something I need to find?

---

### Post by djchandler on 2010-05-07
> **McRat said:**
> I downloaded GoogleEarthLinux.bin (world map app).  I am using 10.04 64bit with Gnome GUI.

When I double click, or right click and open, it says I need to associate it with an application.

Is there an installer app or something I need to find?

It's better to install from a .deb file instead of using the bin. The bin can be run after using chmod to make it executable, but keeping the software updated isn't so simple as using the repositories that have the .deb packages already made for you.

Go to [Medibuntu]("http://www.medibuntu.org/") and there's a whole bunch of closed source / restricted license software available.

Here's the [instructions for adding the repository]("https://help.ubuntu.com/community/Medibuntu").
:guitar:

---

### Post by McRat on 2010-05-08
Thanks!

The only version of this file I can find is from Google, and it's only in a BIN format.  I use it for mapping out outdoor wireless networks.

I changed the attribute so it's executable, but it still says it needs an application associated with BIN files.

---

### Post by djchandler on 2010-05-08
> **McRat said:**
> Thanks!

The only version of this file I can find is from Google, and it's only in a BIN format.  I use it for mapping out outdoor wireless networks.

I changed the attribute so it's executable, but it still says it needs an application associated with BIN files.

I strongly suggest you use **Synaptic Package Manager** or **Ubuntu Software Center** to install the Google Earth application. It may seem like a lot of trouble to add the repository from Medibuntu, but it simplifies future updates. You will get notification through **Update Manager** whenever there's an update.

After adding the repository, simply search for Google Earth in **Ubuntu Software Center **or **Synaptic Package Manager**.

If you don't have superuser rights on your account, that will prevent  executing the .bin installer too. Although _*you may eventually  regret installing this program this way*_, especially as updates  become available, you can execute the .bin file with:
 sudo ./filename

---

### Post by McRat on 2010-05-08
OK, now I get it.  Thanks!

---

