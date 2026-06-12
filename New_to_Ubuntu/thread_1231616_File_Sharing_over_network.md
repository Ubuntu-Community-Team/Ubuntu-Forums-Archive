---
title: "File Sharing over network"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Dave.E on 2009-08-04
Hi,
On attempting to share a folder whilst running Ubuntu I get the message:
"'net usershare' returned error 255: net usershare add: cannot share path /media/115Gig/Documents and Settings/Dave/My Documents/Azureus as we are restricted to only sharing directories we own.
Ask the administrator to add the line "usershare owner only = false" to the [global] section of the smb.conf to allow this."
 
I eventually discovered how to search for files! (I'm totally green to Ubuntu & Linux) only to find there are 4 or 5 'smb.conf' files, and looking at them I'm not at all sure where or how to insert the command.
 
Any help gratefully accepted.
 
Dave.

---

### Post by bodhi.zazen on 2009-08-04
Are those shared directories on Windows or Ubuntu ?

See if this helps : [Samba Server]("https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html#id2540411")

You need to be the owner of the files you are wanting to share.

---

### Post by Dave.E on 2009-08-04
> **bodhi.zazen said:**
> Are those shared directories on Windows or Ubuntu ?

See if this helps : [Samba Server]("https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html#id2540411")

You need to be the owner of the files you are wanting to share.
Ahh OK... 2 hard discs in the PC one is windows one is Ubuntu.
I'm booted from the Ubuntu disc.
Ubuntu can quite happily see all my windows shares on my other PC's over my network.
I want my other PC's to be able to get at stuff on the windows disc as it can when I boot from windows.
Ubuntu can see the disc and it's contents no problem, it's just the network share I want to be able to set up.

Hope this makes sense!

---

### Post by bodhi.zazen on 2009-08-04
I am assuming your windows partition is mounted at /media/115Gig/

In which case you need to unmount it and re-mount is so that you are the owner.

mount -t ntfs-3g /dev/sda1 /media/115Gig -o username=you,umask=000

Change your "dev/sda1" to the actual partitoin and "username=you" to username=yoru log in name

See also : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Dave.E on 2009-08-04
er, thank you... I think!
You are correct about the path 'mounted at'? /media/115Gig
(sorry, us beginners aren't too hot on what mounting means!)
I started Gparted which shows /dev/sda1 does have the label 115Gig
I know my username OK so all I need to know now is how & where to issue this "mount" command?
And will this be a one off or is there a way I can get Ubuntu to do this mount each time I boot instead of /media/115Gig/
Sorry to be a pain, but what is the reason I cant just change or become the owner of /media/115Gig/ ?

Cheers,
D.

---

### Post by bodhi.zazen on 2009-08-04
The reason you can not change the owner of your windows partition is that ntfs (and FAT) do not support such things.

So ownership and permissions are set at the time a partition is mounted.

So open a terminal and enter

sudo umount /media/115Gig

sudo mount ... # The command I gave you.

To set permissions on the partition you need to edit /etc/fstab

see the link I gave you, it is long, but should walk you through the process.

---

### Post by powel212 on 2009-08-04
In add/remove install "NTFS Config" and then launch it "system/Administration/NTFS configuration Tool" Then you will automatically mount your windows drive on boot.

Then 

1.) install system-config-samba

```
sudo apt-get install system-config-samba
```

2.) configure system-config-samba

configure it

```
sudo system-config-samba
```

click add folder - make it writable and visable and under access make it accessible to all users to let the windows box access this new share folder.

3. under preferences\security change auth mode to "share"
then change the guest account to your ubuntu user name and you are done.

Once you reboot you will have shared folders working and all your drives mounted. This should take care of your troubles

I hope that helps

Powel

---

### Post by Dave.E on 2009-08-04
Hmmmm...
Just done all that...
after I'd umnounted it, 115Gig no longer existed so I found out how to make the directory in /media and re-created it.
Then I did the mount which worked.
But I still have exactly the same problem.
I just went back into my window & the directory /media/115Gig still says it's owned by 'root' or doesn't that matter?

The original error was saying that the folder I was trying to share wasn't owned by me.
So I went to that folder in the terminal window & I see it is still owned by root?
" 7372 drwxrwxrwx 1 root root    53248 2009-08-02 13:14 Azureus"

Did I do something wrong?

---

### Post by Dave.E on 2009-08-04
(my last reply was to Bohi, I've not tried what Powel says yet.)

---

### Post by bodhi.zazen on 2009-08-04
> **Dave.E said:**
> Hmmmm...
Just done all that...
after I'd umnounted it, 115Gig no longer existed so I found out how to make the directory in /media and re-created it.
Then I did the mount which worked.
But I still have exactly the same problem.
I just went back into my window & the directory /media/115Gig still says it's owned by 'root' or doesn't that matter?

The original error was saying that the folder I was trying to share wasn't owned by me.
So I went to that folder in the terminal window & I see it is still owned by root?
" 7372 drwxrwxrwx 1 root root    53248 2009-08-02 13:14 Azureus"

Did I do something wrong?

re-mount the partition changing the owner to you

mount /dev/sda1 /media/115Gig -o uid=you,gid=you,umask=000

---

### Post by Dave.E on 2009-08-04
Oh bugger!
It's now 2:35am here in the UK, and this has all become a nasty mess as I feared it might....
Before I saw Bodhi's last message I decided to try Powels method to see if I could get that working.
Samba has installed and I'm sure I did all the things mentioned, however even though my windows laptop can see the shared folder on the Ubuntu machine, when I try to open it I'm told I don't have permission.
I'm not asked for a password or username, I'm just refused access......

Do I now try to reverse the whole SAMBA thing & try changing the owner like Bodhi suggests?
or can I still do that now WITH Samba installed?
should I stick with trying to make SAMBA work?

Do you guys disagree about how this should be done?

I only want read access to the files in that folder yet it seems impossible to make it happen... :(

I really do want to move away from microsoft OS but things like this really do tempt me to just go back to what I know works fine...

I'll sleep on it & see what replies are here when I awake.

Please don't think I'm not grateful guys, your help is much appreciated, just a little frustrated here that's all!

D.

---

### Post by bodhi.zazen on 2009-08-05
The other question is, are you running a firewall on Ubuntu or your windows boxes ?

---

### Post by Dave.E on 2009-08-05
No firewall that I'm aware of...
As well as the folder I can't access there is also an Ubuntu shared folder which I have no problems accessing, so I'm assuming there's no firewall problems.

---

### Post by powel212 on 2009-08-05
Check your samba settings. I have included some pics to help. Where you see my user name "drock" please substitute your own user name". I have set up many systems this way and it works very well. 

samba settings can be found at "system\administration\samba"

See attached.

i hope that helps

Powel

---

### Post by powel212 on 2009-08-05
BTW here is what the windows side looks like on my home network.

Powel

---

### Post by Dave.E on 2009-08-05
Hey thanks Powel!
I double-checked and changed a few things & re-booted both machines and eventually got it working.
Weird thing is though the windows laptop couldn't see the Ubuntu box at all until the Ubuntu box looked at the Windows laptop, only then did the Windows laptop start to see the Ubuntu box & it's shares.

That's no big deal though.

Thanks for all your patience.

I'll now move on to my next question, but I guess I should start a new thread.
Cheers,
Dave.
xxx.

---

### Post by powel212 on 2009-08-05
Now that you mention it I remember experiencing what you just mentioned and I believe it is because the ubuntu box does not announce itself to the router, (which then registers its ip), until after it makes a call out to the network. where as windows is constantly announcing itself, which can be dangerous if you are on an unprotected wireless system.

What's your next question?

Powel

---

### Post by Tux118 on 2009-08-05
Thanks, I was having the same problem. You should make a tutorial for this.

---

### Post by powel212 on 2009-08-05
A good point. It did take me some time and doing to find this working method. I hope that Karmic will address these issues. If this is not the case I will certainly take the time to do a detailed tutorial on the subject. 

Powel

---

