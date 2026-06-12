---
title: "Old ubuntu box as web server"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by jamieh on 2008-08-29
Okay where do I start?

I have an old(ish) computer with Ubuntu 8.04, and I have a Mac Pro. I have made an iWeb site on the Mac Pro. Can I upload the iWeb site to the Ubuntu box and host it there? How would I go about doing this?

Thanks

---

### Post by gnuwatch on 2008-08-29
copy and paste your website files in for web server folder that appache web server will serve.  (you will need to install apache for ubuntu).

---

### Post by jimv on 2008-08-29
Well, first you need the Apache web server on your Ubuntu box.  To get that, you can either look for the Apache2 package in the Synaptic package manager, or run this command in a console:

```
sudo apt-get install apache2
```

Then you need to go save your iWeb site files to a disk, or to a network share accessable by the Ubuntu machine.  Basically, we need to get these files onto the Ubuntu machine somehow.

Once on the Ubuntu machine, the files need to be placed in /var/www.  Once they're in there, you should be able to type in the name of your Ubuntu server in your web browser and see your iWeb page.

If you want the site accessible to people on the internet, you need to go onto your router and forward port 80 to the Ubuntu machine.

---

### Post by jamieh on 2008-10-18
> **jimv said:**
> Well, first you need the Apache web server on your Ubuntu box.  To get that, you can either look for the Apache2 package in the Synaptic package manager, or run this command in a console:

```
sudo apt-get install apache2
```

Then you need to go save your iWeb site files to a disk, or to a network share accessable by the Ubuntu machine.  Basically, we need to get these files onto the Ubuntu machine somehow.

Once on the Ubuntu machine, the files need to be placed in /var/www.  Once they're in there, you should be able to type in the name of your Ubuntu server in your web browser and see your iWeb page.

If you want the site accessible to people on the internet, you need to go onto your router and forward port 80 to the Ubuntu machine.

My cheapskate ISP blocks port 80. so I have to use 8000.
Thanks though it works as long as I put :8000 at the end of everything -_-

---

