---
title: "Samba: getting started and multiple users from windows"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by diyfiesta on 2008-03-30
Hi All,

I managed to get basic Samba running on K/Ubuntu, I have three shares; Me, the Wife and "shared". I've been using Kubuntu and kcontrol to set things up, I added specific users to the shares and (hopefully) by default reject anyone else seeing the shares.

The problem i have is it seems I can access at most one share from a windows machine... so for example, I can log in as me to my share and access it fine. My wife can do the same, I can even unmap my share in windows and log in as her to see her folder. But not both. Any neither of us can manage to access the "shared" folder. Sounds wierd.

I added two users to the smbpassed jobbie. In all cases when logging onto the shares via windows I need to supply a username and (smb) password (for example, \\192.168.0.1\toby).

So my two questions are really

1. Can you point me to a howto or give general tips of setting up my shares securely. Any ideas why I can't access two? Even as the same user? (I understand that accessing two shares, both as different users is somehow difficult in windows, but I'm accessing two shares with the same user, or at least trying to).

2. Any tips of how to assess if my shares are secure? Its on a wireless network.

Thanks muchly for any tips.

All the best,
Toby

ps, some parts of the smb.conf file showing the shares is below;

> 
[toby]
valid users = toby,root
read list = root
write list = toby
invalid users =
case sensitive = no
strict locking = no
msdfs proxy = no
comment = Toby's Share
path = /mnt/share/toby/

[maria]
case sensitive = no
strict locking = no
msdfs proxy = no
path = /mnt/share/maria
comment = Maria's Share
valid users = maria,toby,root
read list = root
write list = maria,toby
invalid users =

[shared]
valid users = toby,maria,root
write list = toby,maria
case sensitive = no
strict locking = no
msdfs proxy = no
comment = Shared pictures etc
path = /mnt/share/shared/
read list = root
invalid users =



---

### Post by Eiríkr on 2008-03-30
For one, I'm not entirely sure from your description if this is the issue, but Windows is rather aggressive when it comes to caching share authentication data (username and password).  Forum user KennedyM wrote up [thread=720889]this HOWTO[/thread] for resetting Windows share caching.  

----------
Now, looking over your smb.conf file, I note a number of bogus options that make me think you might have used a GUI config tool at some point -- these are sadly very unreliable, and I have yet to see a smb.conf file that's been run through a GUI config tool and is still 100% valid and usable.  I'll go over your options here, commenting only on the noteworthy ones:

**[valid users](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#VALIDUSERS) = toby,root**

Judging from the examples in the relevant man page section, linked to in the option name, it looks like the list here should be separated by a comma *and* a space.  


**[strict locking]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#STRICTLOCKING") = no**

Likely unneeded.  From the man page section:

>  This is an enumerated type that controls the handling of file locking in the server. When this is set to yes, the server will check every read and write access for file locks, and deny access if locks exist. This can be slow on some systems.

When strict locking is set to Auto (the default), the server performs file lock checks only on non-oplocked files. As most Windows redirectors perform file locking checks locally on oplocked files this is a good trade off for inproved performance.

When strict locking is disabled, the server performs file lock checks only when the client explicitly asks for them.

Well-behaved clients always ask for lock checks when it is important. So in the vast majority of cases, strict locking = Auto or strict locking = no is acceptable. 

So you probably don't need this option, and should be okay leaving this out (i.e. the server will use the default of "auto").  No biggie, but something to think about.  


**[msdfs proxy](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MSDFSPROXY) = no**

This one is definitely borking all of the share definitions you've posted.  As noted in the man page section:

> This parameter indicates that the share is a stand-in for another CIFS share whose location is specified by the value of the parameter. When clients attempt to connect to this share, they are redirected to the proxied share using the SMB-Dfs protocol.

Only Dfs roots can act as proxy shares. Take a look at the msdfs root and host msdfs options to find out how to set up a Dfs root share.

*No default*

Example: [font=courier]*msdfs proxy = \otherserver\someshare*[/font] 

So it's very unlikely that you need this at all to begin with, and even if you *did*, the option value would have to be a path.  The value you've got here of "no" is a non-existent path, and is screwing up your Samba server.  Delete all of these [font=courier]msdfs proxy[/font] lines.  
----------

HTH,

Eiríkr

---

### Post by diyfiesta on 2008-03-31
Thanks for the tips, I did indeed use the GUI (in kcontrol) and haven't editing the file manually at all!

I'll give those changes a spin tonight when get home :)

Cheers
Toby

---

### Post by Eiríkr on 2008-03-31
If that still doesn't work, please post your full smb.conf file, as the problem might be in your [global] options.  

Cheers,

Eiríkr

---

