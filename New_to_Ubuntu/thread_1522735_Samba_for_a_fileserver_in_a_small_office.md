---
title: "Samba for a fileserver in a small office"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by imfunny on 2010-07-02
Hello everyone!

While I am not new to ubuntu or the command line, I am fairly new to networking and servers. 
So, I was just wondering if anyone could help answer a few question I have or point me in the right direction, thanks!

So I have done some researching and I discovered that Samba might be what I am looking for as the small office is composed of 3 Windows XP Pro Computers and 1+ XP Pro Laptops. They are all currently in a workgroup and are sharing files from one computer so access time is pretty dismal. So I want to take an old computer that is lying around and turn it into a file server and backup (RAID mirror possibly) to help them out.

So, is this the best solution? Any other idea? And how do I go about connecting the file server in with the existing modem, router, switch, etc.

Thanks again!!

EDIT: oh and I was also wondering what would be the best way to partition the disk? i.e. how much space to give to '/' and '/home', etc.

---

### Post by amauk on 2010-07-02
Yep,
Samba is the way to go

It's been a while since I had anything to do with Samba, and sharing to windows boxes
but there's a ton of help there (just google for samba tutorials - make sure they're relatively up-to-date)

basically, your linux server will show up on Windows' network neighbourhood, and your windows clients can access it by the usual
\\servername\folder_share
or, you can map the above to a drive letter for ease of use

> **imfunny said:**
> EDIT: oh and I was also wondering what would be the best way to partition the disk? i.e. how much space to give to '/' and '/home', etc.
From your initial post, you're not doing anything complex
you're just providing centralised shared folder(s) across your network

so it really makes no difference how you partition the disk
(Your server will only have one user, so /home will only have one subdir)

---

### Post by imfunny on 2010-07-02
oh okay, awesome! Thank you very much.

I have just found a good basic tutorial!

And about the partitioning thing, I was just wondering if it would be beneficial to partition the system files separate from the user files...or if ubuntu does this automatically.

---

### Post by pricetech on 2010-07-02
I have a server set up that holds a software repository for installing and updating windows boxen.  Here's a thumbnail sketch of how it's set up:

I have /home on a separate drive from the rest of the OS.  I didn't do software RAID at the time, but when the time comes to replace the box, I will.

The main directory is /home/shares.  Within that are several more directories such as /thirdparty /microsoft /software /printdrivers and so on.

I share /home/shares to administrators only, read / write.  This is how I access the shares from a windows box to update the software in the repository.  The rest are shared read only to everyone so I don't have to bother with credentials when I'm working on a new install for example.

When setting up a computer, I load a program written by one of our IT guys that calls the executables for the software I install, though I can just as easily run it directly from the network or a mapped drive.

I map a drive to the printdrivers share when I need to install a printer.

It works like a charm.

In your case you'll probably want to create shares for your users and maybe a common share or two.  You'll want them read / write of course, shared only to the user or users who need that access.  If you happen to have, for example, standard forms or templates they need to be able to use but not change, you can put them in a read only share.

Just some ideas that should work.  Your mileage will of course vary according to your specific environment.

Good luck and have fun with it.

---

