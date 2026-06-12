---
title: "File and Folder sharing between Windows 7 &amp; Ubuntu 10.10"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by Shah.Nazar on 2011-03-10
I have installed a windows 7 ultimate on desktop with file and print sharing enabled, in work group.
I have installed Ubuntu 10.10 on Net book and also installed Sama.

Windows 7 can see and open any file and folder shared in Ubuntu.
Ubuntu can see windows 7 work group and file and folders, but clicking on any folder to see the content raising an error, cannot mount server.

I have tried many ways and suggestions all around the internet, but no luck yet.

If somebody already came cross this issue and solve it, please give me the hit and direction.

Your help much appreciated.

---

### Post by coffeecat on 2011-03-10
Have a look in the first post in this thread:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Scroll down to the "Windows 7 configuration" heading. There are several things to check there, but I believe needing to disable HomeGroup file sharing is a common issue.

---

### Post by Shah.Nazar on 2011-03-12
I have tried, but still the same issue.
In windows 7 machine, I remove home group and turned on sharing without any home group or work group but ubuntu can see the machine but can not see shares. It's weird. I tried to create a new home group and shared just one simple directory and in security tab I have add GUEST account with full control. This time ubuntu can see machine and can see shared but double clicking on shared folder raising error, "CANNOT MOUNT....." even I have tried manually mount, doesn't work.

It's about 3 weeks ago, I saw a solution in Internet and it was so simple and it worked but I had to re-install ubuntu for some reason and unfortunately I forgot to bookmark that site, I lost it.

Any other idea or thought?
tnx

---

### Post by Mark Phelps on 2011-03-13
Let's stop mixing terms ...
Home Group and Work Group are entirely different things.

Home Groups were introduced in Win7, and NOTHING other than Win7 is able to use them, not even Windows Vista.  So, if you're using Home Groups, there is no way to share that stuff outside of Win7.  Period.

Work Groups have been around since the XP days, and they CAN be shared.

---

### Post by Shah.Nazar on 2011-03-14
Then lets assume I have created a WORKGROUP in windows 7 with enabled file and print sharing, enabled network discovery, disabled password and 128 encryption. What's the next step to make ubuntau able to see and mount windows shares?

tnx

---

### Post by GWBouge on 2011-03-14
I get the 'Unable to mount location, Failed to retrieve share list from server' error when trying to connect through the Network bookmark in Nautilus, but to get around it I can typically goto:

Places -> Connect to Server
Service Type: Windows Share

And enter the IP address.  Or, alternatively, hit Ctrl+L in nautilus and enter 'smb://xxx.xxx.xxx.xxx', where x is the local IP (might work with computer name?)

---

### Post by piquat on 2011-03-15
> **GWBouge said:**
> I get the 'Unable to mount location, Failed to retrieve share list from server' error when trying to connect through the Network bookmark in Nautilus, but to get around it I can typically goto:

Places -> Connect to Server
Service Type: Windows Share

And enter the IP address.  Or, alternatively, hit Ctrl+L in nautilus and enter 'smb://xxx.xxx.xxx.xxx', where x is the local IP (might work with computer name?)

After you mount it, drag the location bar down to the lower left pane.  It will allow you to save a link in Nautilus to go straight there w/o having to type that next time.

---

### Post by Shah.Nazar on 2011-03-15
Hi GW, I've tried this method many times and ubuntu keep asking password for WINDOWS 7 WORKGROUP, when I enter the correct password, still keep asking and when I enter nothing for password, it says cannot mount. In windows 7 machine, I gave access to shared folder to EVERYONE, GUEST with full control. I turned off windows firewall and ...... but nothing, still cannot see and mount windows 7 shared folders.

---

### Post by mastablasta on 2011-03-15
password has to be from windows. 
 
it acts up sometimes. try to connect from Windows to Ubuntu.

---

### Post by Shah.Nazar on 2011-03-15
You right, password is coming from windows and that I mentioned, I know my password for windows workgroup, but ubuntu doesn't like it and keep asking for password.

I have created a shared folder in ubuntu and windows 7 machine immediately recognize it and able to see and brows the content.

Then lets summarized it:

1. Sharing from Ubuntu 10.10 Desktop with windows 7 Ultimate, works, means, windows is able to see and brows the content of ubuntu shared folder/file

2. Sharing from windows 7 Ultimate with Ubuntu 10.10 Desktop, doesn't work, means, ubuntu is not able to see/mount windows 7 shared file and folder.

---

### Post by emptybb on 2011-03-15
> **GWBouge said:**
> I get the 'Unable to mount location, Failed to retrieve share list from server' error when trying to connect through the Network bookmark in Nautilus, but to get around it I can typically goto:

try to disable windows firewall...

---

### Post by GWBouge on 2011-03-15
> **piquat said:**
> After you mount it, drag the location bar down to the lower left pane.  It will allow you to save a link in Nautilus to go straight there w/o having to type that next time.

I don't really use the shares enough to necessitate a bookmark.  Hardly ever, actually ... I just set up shares for those 'just in case' moments, lol.  But a good tip!

> **emptybb said:**
> try to disable windows firewall...

I did ... had the box completely open (no a/v or firewall), no passwords (for shares or login), shared to Guest/Everyone with full control, and still was not able to get to it through Network.  But the smb:// method works for me without issues, so I just do that.  Absolutely *hate* fussing around with networking in Vista/7, lol.

But I'm not trying to get help, Shah is, just wanted to suggest another method of connecting if he hadn't tried it =o)

---

### Post by crispy_420 on 2011-03-16
This may seem odd but change your network type from HOME to WORK network on your Windows 7 box (three options: Home/Work/Public). This solved my issues with PS3 streaming. I think this changes the way files are shared. Home being the idiot proof networking they pushed in adds but it takes a hit in backward/crossplatform compatibility.

Just my humble suggestion and it is worth a shot right?

---

### Post by Steve R. on 2011-06-03
We are having the same issue.  A Sony Vaio 64bit laptop running Window7 won't connect to the home network.  Fumbled around for a while, but nothing worked.

By any chance has the release of Service Pact #1 for Windows 7 resolved any of these network issues???

---

### Post by slyspring on 2012-04-28
I am using Ubuntu 11.10 64-bit. This is the only post i could find to help the masses.

OMG! I just solved this in 15 minutes with just SAMBA and a few Win7 tweaks! Follow these to the letter

1. Using Ubuntu, open Terminal and run **sudo apt-get install samba**

2. Run the command sudoedit **/etc/samba/smb.conf**

3. Under "Global Settings", where it says #Change this to the Workgroup/NT-domain....#, change the workgroup the actual name of your group. Also, add the string directly underneath that called **netbios name = ** and type the EXACT name of your computer.

4. Hit CTRL and the letter X at the same time to exit. When, asked to save, press the letter Y, and hit Enter.

On to Windows 7 (bane of existence)

1. Open Network and Sharing Center.
2. On the left, click "Change Advanced sharing options"
3. Perform the following (make sure your computer is set for Home/Work):
  a: Network Discovery - On
  b: File and Printer Sharing - On
  c: Public Sharing - On
  d: file sharing connection - 128-bit encryption
  e: password protected sharing - off
  f: use user accounts (just as a precaution)
4. In the Control Panel, select User Accounts.
5. Enable the Guest Account. It is not automatically a part of every folder for permissions sake.
6. On the in the folder permissions (or the root of the external drive you want to share), add the Guest account, and I recommend you give it up to MODIFY rights to all folders and subfolders you need. NTFS permissions trump Share permissions.
7. Create the share you want, with me STRONGLY recommending adding the Group user and giving it up to Modify rights. 

All that other crap about winbind and nss... i undid on my Ubuntu, and my fixes persisted forever. take it or leave it.

---

### Post by Morbius1 on 2012-04-28
> Also, add the string directly underneath that called **netbios name = ** and type the EXACT name of your computer.You might want to modify that line somewhat.

The netbios name is automatically set to the host name by default. You can prove it to yourself by running the following command:
```
testparm -sv /dev/null | grep "netbios name"
```That will show you the default setting for that parameter - the settings before you modify them with smb.conf. It should already be set to your hostname.

The problem with "netbios name" is that it can only be 15 characters or less in length. More than that and it's invisible to the LAN.  So if the user has one that's 16 characters long and adds it to smb.conf it won't do any good. So I would recommend that the user count the number of characters in his hostname and if it's 16 characters or more in length add a shorter name to smb.conf with the "netbios name" parameter. If it's 15 characters or less he can add it to smb.conf if he wants but it's unnecessary since it's already in the defaults.

---

### Post by slyspring on 2012-04-28
It was not in mine. only workgroup was in the smb.conf file. I had to add that myself.

---

### Post by Morbius1 on 2012-04-28
> It was not in mine. only workgroup was in the smb.conf file. I had to add that myself.     
Sure it was you're just not looking in the right place. The default setting for netbios name is not in smb.conf. In fact the majority of the default settings for samba are not in smb.conf.

Smb.conf is used to add to or modify the default settings of samba. It's not a listing of all of the defaults - just the modifications.

To see the whole list of default settings before smb.conf modifies any of them:
```
 testparm -sv /dev/null
```In that list will be your netbios name that was automatically set to your host name when you did your original install.

---

### Post by slyspring on 2012-04-28
I see what you mean. Your command gets your computer's name so you can stick that into Samba.

---

### Post by Morbius1 on 2012-04-28
My point though is that the netbios name has already been set to your host name. Samba / Linux does this automatically. There's never a reason to add netbios name to smb.conf unless you are trying to solve the 15 character size limit or you want a netbios name that's different from your host name.

---

### Post by slyspring on 2012-04-28
What I am saying is this:

1. I am running Ubuntu 11.10 64-bit.
2.  Before my fix, I had the same issues as the world apparently.
3. After a fresh install of Samba, the netbios string was not underneath the workgroup string in the smb.conf file, so I had to physically add it.

---

### Post by Morbius1 on 2012-04-28
[COLOR=Blue]**The netbios string was already in the defaults - that's why it wasn't in smb.conf.**[/COLOR] I've given you a way to verify it for yourself so that you don't have to take my word for it. I don't know how to explain it any other way.

Your original statement:
> Also, add the string directly underneath that called **netbios name = ** and type the EXACT name of your computerIf the name of your computer is 15 characters or less then adding it to smb.conf will do nothing since it's already in the defaults ( Remember smb.conf is not the defaults ). If you want to add it anyway it's fine with me.

But, If the name of your computer is 16 characters long or longer then your machine is invisible. If you add netbios name with " the EXACT name of your computer", it will not resolve the problem. It must be 15 characters or less in length.

How about a compromise? Add one more line to your Mini HowTo - so that it looks something like this:
> Also, add the string directly underneath that called **netbios name = ** and type the EXACT name of your computer. [COLOR=Blue]But if your computer name is 16 characters or more then shorten the netbios name to something 15 characters or less.[/COLOR].

---

### Post by slyspring on 2012-04-29
Agreed, as Microsoft Windows has that limitation as well.

---

### Post by CharlesA on 2012-04-29
Hi,

The only thing I have done on a clean install of 12.04 (and 10.04 for that matter) is add my share definitions to smb.conf.

None of the sharing settings were changed on Win7 and they connect fine for me.

Maybe it's cuz I am running a local dns server instead of relying on broadcasts for name resolution.

I have my tutorial up on my site here:
[http://charlesa.net/tutorials/debian/debiansamba.php](http://charlesa.net/tutorials/debian/debiansamba.php)

---

### Post by Morbius1 on 2012-04-29
@CharlesA,

I personally think that the default method of having the netbios name automatically becoming the host name and having it automatically broadcast that name to the network is nothing short of elegant.

The 2 biggest problems with it though is:

** The Ubuntu installer has a tendency to create a host name that's too long. In fact there was a bug report submitted about that: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/735072](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/735072)

** The name resolution order has the broadcast method listed last.
The default is:
> name resolve order = lmhosts wins host bcastIt should be:
> name resolve order = bcast host lmhosts winsBut I like you have not had a problem with the default settings despite having multiple workgroups, not disabling Win7's homegroups, not installing winbind, and everything else that's usually posted.

---

### Post by CharlesA on 2012-04-29
> **Morbius1 said:**
> @CharlesA,

I personally think that the default method of having the netbios name automatically becoming the host name and having it automatically broadcast that name to the network is nothing short of elegant.

Indeed. It means you don't need to run a local dns server or add each host to the hosts file to get name resolution.

> The 2 biggest problems with it though is:

** The Ubuntu installer has a tendency to create a host name that's too long. In fact there was a bug report submitted about that: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/735072](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/735072)

Yep. I've had the installer give me the default name of "Ubuntu-virtualbox" when I installed it on a VM and that would cause issues with Samba if I used the default config.

> But I like you have not had a problem with the default settings despite having multiple workgroups, not disabling Win7's homegroups, not installing winbind, and everything else that's usually posted.

Indeed. It's funny how some things work fine without having to jump thru the hoops that most people have to. I don't know why mine works the way it works but it worked that way when I was running 10.04 and still works the same with 12.04 with no changes to smb.conf outside of the share definitions.

As for the default  resolve order - I totally agree it should be bcast first, but that may cause issues on larger networks, but it would be replicating how Windows resolves names without using a DNS server.

---

### Post by Ahari on 2012-05-29
I know this thread has been going for some time, so forgive me for resurrecting it again. I just felt that as a noob I had to share how I solved this issue. Maybe it will help someone who is searching.... and boy did I have to search! This thread kept coming up on Google, so I thought I would add my 2 cents worth for the benefit of others.

Apart from all the usual fixes that are mentioned here, I found that I had to add a Guest account in Windows 7 for anything to work. If you don't have a Guest account, then nothing will work!

It was such a simple solution, but it works. So if you are having troubles with sharing files, start with making sure you have a simple Guest account on the Windows machine! Then try all the other stuff.

I don't know why this is the case, maybe someone with more knowledge can shed some light on this, just try it....;)

---

