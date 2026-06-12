---
title: "Shared folder not visible to network devices"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by ianp5a on 2010-01-18
I wish to share my Music and Pictures folders on the network. I have an internet Radio and a digital picture frame that can access the windows PCs and the NAS storage successfully.

Problem: The folders do not show up on either device.

I have installed Samba and shared the folders as visible and any user access. I have also right clicked them and shared them with "Sharing options" for good measure. The folders are on an internal NTFS HD.
Note: They show up on a Windows PC but need my Linux password to access them.

Also I right clicked the folders, Properties->Permissions and tried to allow "others" access. However the Access always jumps back to "None"

Has anyone any suggestions how to give access to any user and make them visible to devices that do not have a user.
Thanks.

---

### Post by Morbius1 on 2010-01-18
You're not going to like this because it involves the terminal and those pesky text files, but could you post the output of the following commands please:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**
Type **cat /etc/fstab**

You seem to be using two different methods to share those folders so one of them may have to go.

It could be a permissions error which will require a tweak to your fstab.

---

### Post by Morbius1 on 2010-01-19
For the benefit of anyone else that stumbles on this post let's see if anyone can diagnose and "fix" some of the problems described in the original post without any additional information.
[I]
[1] Sharing Methodology[/I]
> I have installed Samba and shared the folders as visible and any user access. I have also right clicked them and shared them with "Sharing options" for good measure.There are two completely different methods of sharing folders in Ubuntu: Nautilu-Share (right click > Sharing Options in Nautilus ) and Classic Samba. If you're really careful you can use both methods but I would recommend  against using both on the same folder as this user has done. Since this user is allowing guest access and since Nautilus-share is by far the easier of the two methods to use I would get rid of the Classic shares.

*[2] Permissions*
> Also I right clicked the folders, Properties->Permissions and tried to allow "others" access. However the Access always jumps back to "None"I'm fairly certain that the reason for this behaviour is that:
> The folders are on an internal NTFS HD.Linux cannot change permissions on an NTFS partition outside of a mount or by auto mounting through fstab. One way to fix this problem is to alter the fstab entry to allow "others" to read / write to that directory. But in the context of this situation there is another way:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add a line to the [COLOR=Blue][global][/COLOR] section of that smb.conf file that looks like this:

**force user = your_login_user_name**

Save the file, exit gedit, and back in the Terminal type:

**sudo service samba restart**

When the remote user is granted access by samba it will appear to linux to be you ( at least as far as that share is concerned ).

[3] Other Issues

There may be other problems with the setup here but without more detailed information I don't know how anyone can be of further help. I think that if we're luck this might fix the windows to linux problem of asking for a password to access a guest share. But whether or not any of this "fixes" the real problem of the internet devices not "seeing" the folders I cannot say. I don't even know what an internet radio is. ;) What do you think?

---

### Post by ianp5a on 2010-01-20
Thanks M. I'll get on to all this when I'm next home. One thing I particularly want to learn is how to do this via a GUI. I need to learn about those tools in Ubuntu. This is of particular interest for the [Ubuntu Beginners Manual]("https://wiki.ubuntu.com/ubuntu-manual").

It must be possible to open the config files from Nautilus with write privilege instead of starting the terminal, typing, exactly, a special command including the file name. **Does anyone know how to do this?**

By the way, an Internet Radio is like a normal radio set with a dial and a speaker, that gets its music etc. from the internet or local network. They have an ethernet socket and/or a wifi antenna.
They are very popular at the moment. [See them on Amazon]("http://www.amazon.com/s/ref=nb_ss?url=search-alias%3Daps&field-keywords=internet+radio&x=0&y=0").
 
The digital photo frame also has wireless to display photos it finds on my home network (NAS, PCs etc.)

---

### Post by Morbius1 on 2010-01-20
> It must be possible to open the config files from Nautilus with write privilege instead of starting the terminal, typing, exactly, a special command including the file name. **Does anyone know how to do this?**Install the package **nautilus-gksu**
For some reason you need to logoff and then logon again for the package to be imitated.
Then right click a root owned conf file and select "Open as Administrator"

[I]BTW, there are two reasons you're not likely to get instructions for how to do things using GUI's on support forums:
[/I] 
(1) Most GUI's that attempt to configure things like fstab and samba tend to make a mess of things. The people likely to know how to fix things ( or have convinced themselves that they know how to fix things ;) ) know that and tend to do things by hand.

(2) If I want to tell someone new to edit smb.conf as root using a gui I would have to post these steps:

Open Nautilus ( You already have a problem because now you have to explain what nautilus is - doesn't show up on any menu )
Select File System > etc > samba > right click smb.conf > select "open as administrator".

Of course you'll have to tell them to install nautilus-gksu first.

With my short attention span, I as the responder have already forgotten the question ;)

> Open Terminal
Type gksu gedit /etc/samba/smb.confThis is universal and by changing out the gksu and gedit parts to whatever is applicable ( kdesu / kate for example ) will work on any linux distro, or unix, or mac. The gui may change in how it's accessed, it may be different form one release to the next but the terminal will always be the same.

---

### Post by ianp5a on 2010-01-20
> Install the package **nautilus-gksu** 
Thanks. I didn't know about Nautilus Plug-ins! I'll now look out for other interesting Nautilus goodies.

> (1) Most GUI's that attempt to configure things like fstab and samba tend to make a mess of things.
Are you saying bad things about Linux programmers? I'm disappointed. I thought Linux was the way to go. Could this be giving MS a head start?

(2) I understand your point. However my question is not "tell me the steps to follow" it is "how do I fix it myself using a GUI". As I will be getting more familiar with those tools. And I want to know which one is the best for me.
Now that you have told me about Nautilus add-ons, all I need to know is: "edit /etc/samba/smb.conf" which, for me, is progress.

Currently I *still* believe I can do *everything* the easy way. But if my daily maintenance involves using a terminal I'll dump Ubuntu and come back in another few years, as I've been doing for some time.
But thanks anyway for your help.

---

