---
title: "[SOLVED] Is SAMBA the answer"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by DXM31 on 2008-03-11
I want my Ubuntu laptop to access the shared files on my xp desktop.
I have done searches and prolly searched for the wrong things.
I don't really need to share the files on the laptop, there is not much on here.
Thanks

---

### Post by handydan918 on 2008-03-11
Yes. Samba is the answer.

---

### Post by jcwmoore on 2008-03-11
yes, for linux to windows samba is answer

---

### Post by handydan918 on 2008-03-11
> **jcwmoore said:**
> yes, for linux to windows samba is answer

Yeah, what HE said...

---

### Post by DXM31 on 2008-03-11
That's good to know...
How do I do it?

---

### Post by superprash2003 on 2008-03-11
check out the tutorial in ubuntuguide website.. [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by jcwmoore on 2008-03-11
> **handydan918 said:**
> Yeah, what HE said...

hey, I calls 'em like I's see 'em

i'm not ripping off of you, only agreeing

---

### Post by DXM31 on 2008-03-11
> **superprash2003 said:**
> check out the tutorial in ubuntuguide website.. [http://ubuntuguide.org](http://ubuntuguide.org)

Huh...what
Why do have to create a password?
What ever happend to select My Network and oh look my shared files on my desktop?

---

### Post by superprash2003 on 2008-03-11
creating a password is for security!!!so whenever somebody tries to access your shared files they will have to enter username and password

---

### Post by handydan918 on 2008-03-11
> **jcwmoore said:**
> hey, I calls 'em like I's see 'em

i'm not ripping off of you, only agreeing
Heh. Just funnin'....:)

Besides, rip all you want. All my comments are GPL'd...

---

### Post by jcwmoore on 2008-03-11
> **handydan918 said:**
> Heh. Just funnin'....:)

Besides, rip all you want. All my comments are GPL'd...

i hear you...
in my opinion there is nothing worse than being beat to the post with the best answer, but the best answer is the best answer, and lots of people know the best answer, and all of my comments are GLP'd... post off of and rip off all you want...

---

### Post by DXM31 on 2008-03-11
> **superprash2003 said:**
> creating a password is for security!!!so whenever somebody tries to access your shared files they will have to enter username and password

So I have to enter a password for files I am already sharing without a password?
I know this can be a bad word but Vista on this laptop finds the shared files on my xp desktop.
No password.
This is for my local network so unless somebody breaks into my house guesses the password on my WEP...
I don't want another password.
I would like my Ubuntu laptop to see my XP desktop shared files.
Not trying to be rude, just trying to understand why.
Shouldn't this be easy?

---

### Post by Ralf.Nieuwenhuijsen on 2008-03-11
It should be easy. But that bug has been open for years now. They are not going to fix it any time soon.


Go to a terminal.
Enter:

   sudo gedit /etc/samba/smb.conf

Look for the line '#security = user'
Make it so:

 security = share

Then either reboot your computer, or type this in the terminal:

  sudo /etc/init.d/samba restart

As to why? Well, your local network might be separated from the internet by a router, if it's connected _directly_ anybody could be accessing your files. 

Nevertheless, there should exist some solution to just share it read-only in those cases and use a password when you want to be able to delete or add files.

---

### Post by DXM31 on 2008-03-11
thanks thats what I was looking for.
I will give it a shot.:)

---

### Post by DXM31 on 2008-03-11
I changed security to share rebooted SAMBA
There are only the local folders on shared folders
I did notice when I was editing smb.conf that my desktop name was in there.
I'm still missing something.

---

### Post by superprash2003 on 2008-03-12
to share a folder.. right click on the folder and click on "share folder".. then you can choose whether you want it to be read-only or not.. and you can choose the share name!!.. you might have to reboot samba after that!!

---

### Post by Eiríkr on 2008-03-12
A serious point to note, here, writ large so folks can't miss it:

> **DXM31 said:**
> [size=3]**I want my Ubuntu laptop to access the shared files on my xp desktop.**[/size]
I have done searches and prolly searched for the wrong things.
**I don't really need to share the files on the laptop**, there is not much on here.
Thanks

Folks, helping DXM31 set up a Samba *server* on Ubuntu **is most definitely not what we need here.**  Helpful instructions for [font=courier]smbclient[/font] or better yet a GUI way of accessing the XP shares would be more on target.  ([color=gray]NB: I'm not ragging on anyone here, simply trying to bring this thread back on target with something that might be more what DXM31 needs / wants.[/color])

With that in mind, DXM31, most of the instructions so far have been about sharing out the files on your Ubuntu laptop, which, as we remind ourselves above, is not what you want to do.

For accessing your XP shares, open your file browser in Ubuntu, click Go -> Network, and you should see things like your other computers on your network and / or a Windows Network icon.  Click these as appropriate and you should eventually find your shares.  If you run into any problems with this, get back to us, and we can help you from there.  

Cheers,

Eiríkr

---

### Post by Whiffle on 2008-03-12
> **Eiríkr said:**
> A serious point to note, here, writ large so folks can't miss it:



Folks, helping DXM31 set up a Samba *server* on Ubuntu **is most definitely not what we need here.**  Helpful instructions for [font=courier]smbclient[/font] or better yet a GUI way of accessing the XP shares would be more on target.  ([color=gray]NB: I'm not ragging on anyone here, simply trying to bring this thread back on target with something that might be more what DXM31 needs / wants.[/color])

With that in mind, DXM31, most of the instructions so far have been about sharing out the files on your Ubuntu laptop, which, as we remind ourselves above, is not what you want to do.

For accessing your XP shares, open your file browser in Ubuntu, click Go -> Network, and you should see things like your other computers on your network and / or a Windows Network icon.  Click these as appropriate and you should eventually find your shares.  If you run into any problems with this, get back to us, and we can help you from there.  

Cheers,

Eiríkr

Ding ding ding! we Have a winner! 

Anyway.  If the computer doesn't show up in the network, you should be able to put in

smb://hostnameofservercomputer 

in the nautilus/konqueror address bar depending on which one you're using.  If your network is all dandy, that should do it.  If its not, then you can try

smb://ipaddressofservercomputer

ie

smb://192.168.1.151

---

### Post by DXM31 on 2008-03-12
> **Whiffle said:**
> Ding ding ding! we Have a winner! 

Anyway.  If the computer doesn't show up in the network, you should be able to put in

smb://hostnameofservercomputer 

in the nautilus/konqueror address bar depending on which one you're using.  If your network is all dandy, that should do it.  If its not, then you can try

smb://ipaddressofservercomputer

ie

smb://192.168.1.151

**Finally**, two people actually read my post
When I tried the first way I got:

Sorry, couldn't display all the contents of "Windows Network: mshome".

Then I went into mshome and changed the link
to 
smb://HPDESKTOP/  (I know how original)
I get the same message
Have not tried the second way yet as I don't know the IP address of my desktop.
Plus I don't know what the Nautilus/Konqueror bar is
Sorry still a little new at this
Thanks

---

### Post by pbpersson on 2008-03-12
> **DXM31 said:**
> 
Plus I don't know what the Nautilus/Konqueror bar is
Sorry still a little new at this


Konqueror is sort of like Internet Explorer - it is a KDE desktop application that can be used as a web brower but it can also be used to browse files on your local machine.  Actually, it is a great tool that can be used for several purposes and in this case we want to access your Windows XP machine with it.

Konqueror can be found in the "Internet" portion of your application menues and if it is not there, you might need to install it.  I have several Linux machines here and some had it by default and on others I had to add it.

At the very top of the screen you will see an address bar.  To access your remote machine you put in the IP address of the machine along with the share you wish to access.  In my case, I type the following:

smb://192.168.0.64/data

I need to do this using the IP address because there is a bug in the Windows XP computer browser service, it keeps getting flaky.  It will not publish the name of the computer on the network.  I can go running to the other side of the house, get on the XP machine, and stop and start the browser service to fix it.....and then run back in here so the Linux machines can see it....or I can just know the IP address - I took the easy way out.

And.....no, it is not a problem with Linux because the other Windows machines cannot see the Windows XP machine either.  All the Linux machines can see the Windows 2000 machine no problem - 24 hours a day, 7 days a week.  But that is not where my files are located.

Darned Window$......  :(

Anyway, I hope this helps.  :)

OH.....when you get it working, add your remote Windows XP share as a bookmark so you never need to type it again.

---

### Post by DXM31 on 2008-03-12
I just have two questions about this
If I install Konqueor will it mess up my wifi(most things seem to)?
and
How do I find the IP addr of my xp desktop?
Thanks
I forgot to add I use firefox as a browser, I guess that won't work?

---

### Post by Eiríkr on 2008-03-12
... And Nautilus is your default file browser in a standard Ubuntu installation.  The address or location bar is, as pbpersson notes, the same as in Explorer in Windows -- it's the text area towards the top of the window that shows your path.  In Nautilus, for some reason, this bar is often hidden by default, but you can show it pretty quickly by either hitting Ctrl+L, or clicking View -> Location Bar.  

To find your IP in XP, click Start -> Run, type "command" (minus the quotes) and hit Enter, then at the prompt type "ipconfig" and hit Enter.  The output of this command should show you information about your current network connection.  The first or second line should be "IP Address" -- this string of four numbers, something like 192.168.10.101, is what you'd enter into the address bar.  

If you're *really* not worried about security, one sharing option on the Windows side that can make things go much smoother is changing the sharing permissions.  You do this from within XP by right-clicking the shared folder, selecting Sharing and Security, then clicking the Permissions button.  Then in the Share Permissions dialog, click Add, type the word "everyone" (minus the quotes) in the text box and click OK, select Everyone in the "Group or user names" list, and make sure the "Permissions for Everyone" box below has all the correct permissions you want -- Read, Change (i.e. "write" in Unixy terms), and Full Control (not sure what the Unixy synonym is for this one).  Once this is all done, click OK a bunch of times until you're out of the dialogs.  

If you're at all interested regarding the other details of setting up Windows for login- and password-less sharing, have a look at [post=4454301]this post[/post] and look over some of the rest of the thread.  It seems there's a bug in the Samba client code that makes it difficult to properly connect *without* a password, even if the Windows account doesn't have one in the first place, unless you use this "allow everyone" trick on the Windows side.  

HTH (hope this helps),

Eiríkr

PS -- Installing Konqueror shouldn't mess up your wifi, as it's basically just another browser, and won't touch your network settings.  But see if you can get Nautilus to work first, as it's generally better to keep things simple when possible.  ;)

---

### Post by DXM31 on 2008-03-12
I like the idea of not installing something else.
According to SPM Nautilus is installed but I can't find it in app>internet
only firefox show up so it should be somewhere right?

Sorry for all the dumb questions

---

### Post by Eiríkr on 2008-03-12
No trouble, as a teacher of mine once said, the only truly dumb question is one you already know the answer to.  :)

I admittedly don't have the default Ubuntu install (I've got the Xubuntu variety instead for its more pared-down GUI side, since I'm using it for a file server), but I think Nautilus is what should open if you double-click any folders anywhere.  It should say something like "[Current Folder] - File Browser" across the top.

---

### Post by Whiffle on 2008-03-12
Nautilus should be installed by default. Its the program that you get when you open your home folder actually.  I think for some silly reason the address bar is hidden, replaced with some buttons.  There should be an option, possibly in the view menu to change the buttons to an address bar like you'd find in a web browser.  I'd give ya more details but I havn't used nautilus in years...

---

### Post by DXM31 on 2008-03-12
I got it Nautilus is the file cabinet/places
Still trying to figure out how to put in an addr

---

### Post by DXM31 on 2008-03-12
Got it and got them.
WOW this was interesting.
Ubuntu has provided me a lot of opportunity to learn stuff.
You guys have been awesome thanks.

---

### Post by Eiríkr on 2008-03-12
Cool!  Glad to hear it.  And yes, there's a lot of opportunity to learn.  That's one of the things I'm very much enjoying about Linux in general -- you can actually learn what's going on in the system, instead of having to make do with incredibly obscure error messages and idiot help lines.  Yech!  Give me the OSS community wherever possible.  

So if everything is working as you need it, and your issue is resolved, then please also remember to mark this thread as SOLVED in the Thread Tools dropdown at the top of the page.  :)

Cheers,

Eiríkr

---

### Post by DXM31 on 2008-03-12
> **Eiríkr said:**
> Cool!  Glad to hear it.  And yes, there's a lot of opportunity to learn.  That's one of the things I'm very much enjoying about Linux in general -- you can actually learn what's going on in the system, instead of having to make do with incredibly obscure error messages and idiot help lines.  Yech!  Give me the OSS community wherever possible.  

So if everything is working as you need it, and your issue is resolved, then please also remember to mark this thread as SOLVED in the Thread Tools dropdown at the top of the page.  :)

Cheers,

Eiríkr

Will do..still looking for thread tool dropdown, got my glasses on and everything

---

