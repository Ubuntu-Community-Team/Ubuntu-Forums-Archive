---
title: "So just what is Ubuntu's recommended file sharing?"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by ofb on 2010-10-26
I've got two Lucid installs connected by secondary ethernet cards with a crossover. I want full access of the drives on one Lucid from the other Lucid.

Ubuntu file sharing seems to be as problematic as ever. Darn shame, because there was a pretty decent set of GUI for NFS and SMB just a few releases ago.

I've been bashing at this for a some time an have hit the Cross-eyed Frustration level. Please forgive some of that leaking through here. I do know how unattractive it makes help requests.

... Basically I want to know what Ubuntu thinks we _should_ be using. I gave up on Ubuntu LAN some time ago because I got fed up with having it borked with each upgrade. It was easier to use sneakernet.

What we seem to have:

--Personal File Sharing-- New method in the default Preferences Menu. Seems to use Apache. Currently borked with a neglected bug. That's not encouraging, especially when we've already made it to the next release.

--SMB-- Good old Samba. I've got it installed. And it's no good at all for Ubuntu because of the filename mangling for Win compatiblity. 

--NFS-- NFS used to be The Thing for this sort of connection. Ubuntu always seemed to treat it as deprecated, hence trouble with each upgrade. And right now I'm noticing a whole lot of posts about busted NFS after Meerkat upgrades.

Add the usual backdrop of Community Help doc lag, and frustrated user forum requests that go nowhere, typically with the help of well-intentioned people who haven't actually used these functions on the current release. Makes for a lot of noise online, and a lost signal.

... So, what /is/ Canonical's gameplan here? They briefly established a good GUI system for both NFS and SMB, then seemed to move away from NFS in an attempt to simplify the experience around SMB. Now that's gone too and we've got Personal File Sharing, which has apparently been shipped too early, and is perhaps already being neglected in favor of something else.

I'd like to know so whatever I do use will be less likely to be broken by upgrades, and more likely to have a default GUI setup.

---

### Post by ikt on 2010-10-26
> **ofb said:**
> ... Basically I want to know what Ubuntu thinks we _should_ be using. I gave up on Ubuntu LAN some time ago because I got fed up with having it borked with each upgrade.

You couldn't stick a router between the 2?

I've never had an issue with ubuntu and my lan going back as far as 7.04 so I have no idea what you mean by this?

---

### Post by HermanAB on 2010-10-27
Howdy,

The network system is called a 'stack' for a good reason. If the bottom of the stack is broken, then everything on top is broken as well.

So, FIRST get the LAN to work, then worry about FTP, NFS or Samba.  Otherwise you are just wasting your time.

---

### Post by ofb on 2010-10-27
Hi guys. Thanks for stopping by, but you seem to misunderstand. I have a working network. This is a file sharing method question.

---

### Post by yesrno on 2010-10-27
I personally always use Samba. Took me less than an hour to set it up correctly and working like a charm for over a few months now. Don't see the problem with Samba.

---

### Post by ofb on 2010-10-27
As stated, SMB uses filename mangling. This a feature that preserves backward compatibility with old Windows filesystems.

For instance a long filename will be reduced to something like 'HPNGUQ~O.PNG' when you view it across the network, and it will be renamed to that if you bring it over.

I'm not using any Win filesystems, old or otherwise. I'm using ext3 and ext4, and I want a file sharing method that preserves my perfectly legitimate filenames rather than rubbish them.

Otherwise, yeah, SMB would be great. Bit of a surprise it hasn't been extended to do filesystem detection, and only mangle as needed.

---

### Post by ofb on 2010-10-27
Right. I just gave "Personal File Sharing" a go.

It is Apache. Which functionally means no filename mangling, but you're limited to sharing what you put in ~/Public.

So I thought I'd try placing a shortcut inside ~/Public, to see if the client machine can follow those, and get around that limit. However when I try to connect I get this error:

> 
Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)


...and a search of that reveals others complaining about the same thing without solution.

So Canonical may be supplying this method as default now, but they sure aren't supporting the effort with bug fixes. It's been six months since Lucid was released.

---

### Post by ikt on 2010-10-28
> **ofb said:**
> 
...and a search of that reveals others complaining about the same thing without solution.

Has the bug been reported on launchpad?

> **ofb said:**
> 
So Canonical may be supplying this method as default now, but they sure aren't supporting the effort with bug fixes. It's been six months since Lucid was released.

Canonical cannot possibly fix every bug.

---

### Post by jrev on 2010-10-28
as far as I know, Ubuntu provides NFS sharing which I use since the beginning of Ubuntu. It always works fine and I use it to save my personnal files regularly from a computer to another via LAN 
of course the LAN is supposed to be in operating conditions :P

---

### Post by HermanAB on 2010-10-28
NFS is really the best way to network UNIX computers.  You don't need a wizard for that, since it needs only one line of configuration, so a wizard will just make it more difficult, not easier.

---

### Post by mcduck on 2010-10-28
> **ofb said:**
> As stated, SMB uses filename mangling. This a feature that preserves backward compatibility with old Windows filesystems.

For instance a long filename will be reduced to something like 'HPNGUQ~O.PNG' when you view it across the network, and it will be renamed to that if you bring it over.

I'm not using any Win filesystems, old or otherwise. I'm using ext3 and ext4, and I want a file sharing method that preserves my perfectly legitimate filenames rather than rubbish them.

Otherwise, yeah, SMB would be great. Bit of a surprise it hasn't been extended to do filesystem detection, and only mangle as needed.
Never noticed such thing, I'm using SMB all the time to move stuff between my Linux, Mac and OSX machines and all the long filenames work just fine. :)

Check your Samba configuration. (especially the mangled_names option, you'll want to disable that)

edit: I just wanted to add that I haven't actually ever even had to edit the smb.conf myself, on all my systems this already works correctly by default.

---

### Post by ofb on 2010-10-28
> Has the bug been reported on launchpad?

Which bug? The very basic missing packages notification was reported in March. Further trouble past that is plenty of warning to stay away.

Back on topic, I've got the Meerkat CD fired up on another machine. Personal File Sharing has been removed from the menu. 

Right-click a folder for Sharing Options offers to install SMB.

Oh, /this/ is interesting: same thing in Lucid. How could I miss that? Alzheimer's greeting card, I suppose.

But that clears up the question. Canonical is still centering around SMB for basic sharing then.

How terribly disappointing.

---

### Post by ofb on 2010-10-28
Hi guys. Yeah, looking at NFS will be next. I used to use it but had it borked with each upgrade. A quick search of NFS + Meerkat found enough people complaining about similar to make it my last choice this time. But I'm there now

mcduck, There are a number of options to tailor the mangling in smb.conf, rather than one option that turns off all of it. At least as far as I can tell from the documentation. At no point does anything state directly how to turn it right off, just how to tailor it to various win systems.

And therein is my trouble -- I don't understand this well enough to know that just reversing those five or so is enough, and I'd rather not experiment just to find I'm wrong months down the line, staring at a mangled filename and wondering what it should be. I'd like to be sure I've got it right.

I did ask about it previously, but got no answer at that time.
[http://ubuntuforums.org/showthread.php?t=1605119](http://ubuntuforums.org/showthread.php?t=1605119)

---

### Post by freak42 on 2010-10-28
if all else fails, sshfs might be a last resort option, it allows you to mount remote ssh sessions into the local filesystem.

rough steeps needed:

1) make sure you are able to ssh into the machine you want to share files from

2) install sshfs if needed

3) create a mount point for instance in /media/'remotemachine'/

4) execute sshfs
for instance 
```

 sshfs -C -o transform_symlinks -o auto_cache -o idmap=user user@server:/remote/path/to/mount /media/'remotemachine'/ 
```


hth

---

### Post by canoemoose on 2010-10-28
I've got a network with file sharing between Ubuntu, XP, Windows 7 and the occasional OSX client.  It workes perfectly OOTB using Samba - no filename mangling or anything.  Can you not purge your config (perhaps all Samba as well) and reinstall, and see if it works then?

I can't see why you're experiencing problems when nobody else is. :/

---

### Post by mcduck on 2010-10-28
> **ofb said:**
> 
mcduck, There are a number of options to tailor the mangling in smb.conf, rather than one option that turns off all of it. At least as far as I can tell from the documentation. At no point does anything state directly how to turn it right off, just how to tailor it to various win systems.

Well, my point was that unlike what you said, SMB does handle long filenames.

Anyway, try reading this page, it explains the options in a bit more detail: [http://www.faqs.org/docs/samba/ch08.html#samba2-CHP-8-TABLE-5]("http://www.faqs.org/docs/samba/ch08.html#samba2-CHP-8-TABLE-5")

..and in the end, you are not going to break things if you try switching these settings, so it's better to try them and see if it works than not try them and complain about file sharing not working. At least trying them gives you a fair chance of fixing the problem... ;)

---

### Post by mcduck on 2010-10-28
> **ofb said:**
> 
But that clears up the question. Canonical is still centering around SMB for basic sharing then.

How terribly disappointing.
There really isn't a better option, knowing that Windows still lacks built-in support for NFS.

However bad SMB/CIFS is, at least it works across all major operating systems without requiring third-party software.

---

### Post by AndyCee on 2010-10-28
Sorry to post in a closed thread - I was compelled by my own arrogance & need to assist where help was not requested.

Err, I'm sure this is much simpler than the options being discussed. Here are three simple options available by default in Ubuntu via gui.

1. "Connect to server" - option available within "Places" menu. Doesn't seem to have NFS, but works for the other handful of protocols. Even makes a bookmark if you like.

2. "Share root filesystem". In an environment you trust enough to share your root filesystem, you could navigate to the root folder and select "File" -> "Properties" -> "Share" etc. Might need to run nautilus as root ("gksudo nautilus")

3. The obvious one, navigating to "Network", doesn't suit your needs?

---

### Post by AndyCee on 2010-10-28
> **mcduck said:**
> There really isn't a better option, knowing that Windows still lacks built-in support for NFS.

However bad SMB/CIFS is, at least it works across all major operating systems without requiring third-party software.

SMB as a "default" would be more disappointing because it's not native to the platform, and counter-intuitive to use between two linux machines.

Considering Ubuntu is intended for simplicity, it would make sense to have SMB the "default" sharing protocol, easing integration into existing environments. I would never use it in a Linux only environment like the OP described any more than using Microsoft's "Server for NFS" for sharing in a windows-only environment.

---

### Post by ofb on 2010-10-28
AHA!

It's _not_ filename length that's triggering mangling. It's the characterset.

Sorry about that.

It's still a problem, but at least we have the right tree to bark at now.

I've been away reinstalling SMB and playing with different filenames to see what gets mangled. So far it's just characterset issues that trigger it. Quotes, question marks, commas.

These characters are allowed on both the client and the server (I checked), it's just SMB won't pass them.

And good lord, it's 4.30 am. I've got to stop. But does anyone know how to make SMB charset neutral? (Surely this is a problem with multiple language installs?)

---

### Post by ofb on 2010-10-29
-- summary for people who search the forums --


Adding the line 'mangled names = no' to smb.conf solves this problem for the special characters mentioned above. 


Here's my source of confusion:
[http://www.samba.org/samba/docs/using_samba/ch08.html#samba2-CHP-8-TABLE-5](http://www.samba.org/samba/docs/using_samba/ch08.html#samba2-CHP-8-TABLE-5)

"Table 8-5 Name-mangling options" lists nine mangling options. Here's the fifth:

Option - mangled names	
Parameters - Boolean	
**Function - Mangles long names into 8.3 DOS format.**
Default	- yes	
Scope - Share

That's rather specific, isn't the same thing at all.

Whereas here's the relevant portions of 'man smb.conf':

```

       mangled names (S)

           This controls whether non-DOS names under UNIX should be mapped to
           DOS-compatible names ("mangled") and made visible, or whether
           non-DOS names should simply be ignored.

           See the section on name mangling for details on how to control the
           mangling process.

           If mangling is used then the mangling method is as follows:

           ·   The first (up to) five alphanumeric characters before the
               rightmost dot of the filename are preserved, forced to upper
               case, and appear as the first (up to) five characters of the
               mangled name.

           ·   A tilde "~" is appended to the first part of the mangled name,
               followed by a two-character unique sequence, based on the
               original root name (i.e., the original filename minus its final
               extension). The final extension is included in the hash
               calculation only if it contains any upper case characters or is
               longer than three characters.

               Note that the character to use may be specified using the
               mangling char option, if you don´t like ´~´.

           ·   Files whose UNIX name begins with a dot will be presented as
               DOS hidden files. The mangled name will be created as for other
               filenames, but with the leading dot removed and "___" as its
               extension regardless of actual original extension (that´s three
               underscores).

           The two-digit hash value consists of upper case alphanumeric
           characters.

           This algorithm can cause name collisions only if files in a
           directory share the same first five alphanumeric characters. The
           probability of such a clash is 1/1300.

           The name mangling (if enabled) allows a file to be copied between
           UNIX directories from Windows/DOS while retaining the long UNIX
           filename. UNIX files can be renamed to a new extension from
           Windows/DOS and will retain the same basename. Mangled names do not
           change between sessions.

           Default: mangled names = yes

```

```

NAME MANGLING
       Samba supports name mangling so that DOS and Windows clients can use
       files that don´t conform to the 8.3 format. It can also be set to
       adjust the case of 8.3 format filenames.

       There are several options that control the way mangling is performed,
       and they are grouped here rather than listed separately. For the
       defaults look at the output of the testparm program.

       These options can be set separately for each service.

       The options are:


       case sensitive = yes/no/auto
           controls whether filenames are case sensitive. If they aren´t,
           Samba must do a filename search and match on passed names. The
           default setting of auto allows clients that support case sensitive
           filenames (Linux CIFSVFS and smbclient 3.0.5 and above currently)
           to tell the Samba server on a per-packet basis that they wish to
           access the file system in a case-sensitive manner (to support UNIX
           case sensitive semantics). No Windows or DOS system supports
           case-sensitive filename so setting this option to auto is that same
           as setting it to no for them. Default auto.

       default case = upper/lower
           controls what the default case is for new filenames (ie. files that
           don´t currently exist in the filesystem). Default lower. IMPORTANT
           NOTE: This option will be used to modify the case of all incoming
           client filenames, not just new filenames if the options case
           sensitive = yes, preserve case = No, short preserve case = No are
           set. This change is needed as part of the optimisations for
           directories containing large numbers of files.


       preserve case = yes/no
           controls whether new files (ie. files that don´t currently exist in
           the filesystem) are created with the case that the client passes,
           or if they are forced to be the default case. Default yes.

       short preserve case = yes/no
           controls if new files (ie. files that don´t currently exist in the
           filesystem) which conform to 8.3 syntax, that is all in upper case
           and of suitable length, are created upper case, or if they are
           forced to be the default case. This option can be used with
           preserve case = yes to permit long filenames to retain their case,
           while short names are lowercased. Default yes.

       By default, Samba 3.0 has the same semantics as a Windows NT server, in
       that it is case insensitive but case preserving. As a special case for
       directories with large numbers of files, if the case options are set as
       follows, "case sensitive = yes", "case preserve = no", "short preserve
       case = no" then the "default case" option will be applied and will
       modify all filenames sent from the client when accessing this share.

```


That's rather different from the book's presentation. Here "mangled names" isn't one option among many, but is the root option to turn mangling On or Off.

While characters-set differences are not mentioned specifically anywhere, we've got the coverage of a general statement: "This controls whether non-DOS names under UNIX should be mapped to DOS-compatible names ("mangled") and made visible, or whether non-DOS names should simply be ignored."

Here, "ignored" would mean no action is taken that isn't applied to a regular name. The first time I read through, I thought they meant the file would be ignored, as in not displayed on the client, rather than displayed mangled.


So, yeah -- If you've using Samba on a linux<->linux system with ext3 or ext4, you'll want to add that line to your smb.conf.


(It's also worth noting that the book mentions a "mangle case" option. That's not listed anywhere in the smb.conf manpage. Turns out that the book is from 2003, so really shouldn't be used as a reference anymore.)

---

### Post by mcduck on 2010-10-29
> **AndyCee said:**
> SMB as a "default" would be more disappointing because it's not native to the platform, and counter-intuitive to use between two linux machines.

Considering Ubuntu is intended for simplicity, it would make sense to have SMB the "default" sharing protocol, easing integration into existing environments. I would never use it in a Linux only environment like the OP described any more than using Microsoft's "Server for NFS" for sharing in a windows-only environment.

If NFS is default those using Ubuntu in a mixed network will complain, and if SMB is the default those using Ubuntu in Linux-only network will complain. Either way somebody will be unhappy.

However, I'd think it's pretty safe to assume that a person running a network of multiple Linux machines might be more experienced with Linux networking than a person trying to get his Ubuntu box to communicate with Windows/OS X. So choosing the "easy default" with those people in mind makes more sense.

---

