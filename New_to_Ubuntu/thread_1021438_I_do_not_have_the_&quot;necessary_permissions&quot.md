---
title: "I do not have the &quot;necessary permissions&quot;?!?!?!"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Jodha on 2008-12-25
Hi Ubuntu People!

I come from the land of Windows to join you, never back to MicroSoft do I want to go.

However... something perplexes me a lot in my first few days with Ubuntu, and this could cause tensions with my new OS which I otherwise like muchly.

Three scenarios which point to the same problem, any help to sort this would be muchly appreciated :)

1) I have an external HD which I have media backed-up onto. I started doing some directory tidying and this was fine. As I went along the folders started gaining little padlock logos and soon I couldn't move anything onto or around my external HD... because I didn't have the right permissions. Nor could I change these, because I didn't have the right permissions to change the permissions. (!)

2) I install Xampp so I can do some web development. Upon making an alias directory to develop my new websites in I need to modify a config file in the Xampp install directory/etc. When I go to save the changes in this config file I get a message telling me I cant save this file because I dont have "necessary permissions". (!!)

3) I consider using the default folder Xampp sets up to put my webdev in, I go to move my "test.php" file to the Xampp development folder and I get the same kind of error "Error moving file: Permission denied"... probably because I don't have NECESSARY PERMISSIONS (!!!)! :( :( :( :(

WHY!!!! (ahem)

All this time I have going through my head: "I should be telling you what to do, I installed the O/S, I am logged in as me, why do you not at least prompt for password like when installing software? This is stopping me from using this computer"

Can somebody tell me how to sort this out please? I cannot have my computer telling me what I can and cannot access/modify when it comes to my files here.

Many thanks for your time :)

---

### Post by taurus on 2008-12-25
1.  Is your external drive a ntfs filesystem?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

2.  ```
gksudo gedit /path_to_filename/filename
```

3.  ```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by arpanaut on 2008-12-25
This will give you some info on how things work with Ubuntu:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I'd eloborate but I'm heading off to Xmas dinner right now...

---

### Post by Nepherte on 2008-12-25
The user only has full access to his own user directory (/home/username). Anything else requires administrator (root) privileges. The root account on ubuntu is disabled by default, instead they use sudo. With sudo you can temporaryly perform administration tasks. Just put sudo in front of any terminal command or gksudo if it's a graphical application. You can read all about sudo here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo). In your case, when you want to move or delete some files, use
```
gksudo nautilus
```
If you want to edit stuff with a text editor, use
```
gksudo gedit
```
Be careful with using (gk)sudo. Anything requiring sudo priviliges can possible have serious implications to your system.

---

### Post by Temposs on 2008-12-25
hello Jodha,
   I'm glad you've decided to try this lovely OS!

Now, as for your problem, the permissions system in Ubuntu is actually not so hard to work with, once you understand it.

When you are using Ubuntu, files that you create yourself that originated in Ubuntu are created with you as the owner. In this case, you should have no trouble modifying and doing otherwise to those files.

Some files are created by the system or are otherwise not assigned to belong to you. They may be assigned to the system user which is called root, or some other user, if the file came from another computer or something.

In general, Ubuntu recommends that if you want to change permissions for files that don't belong to your user, you should use the "sudo" command from a terminal, followed by the command that you wish to execute with administrator priveleges.

Open yourself a terminal window with Applications->Accessories->Terminal

For example, suppose I have a config file that I want to edit, but the system(root) owns the file. Then, open a terminal to that directory, and type:

sudo gedit somecongif.conf

This will open the text editor and grant it administrator access
Do that for system files that you want to let remain as administrator owned.

If on the other hand you have files like the ones on your external hard drive that you want to belong to you, do this:

sudo chown myusername myfile

chown will change the owner of myfile to myusername, if myusername is my user name.


I hope this is helpful!

---

### Post by Jodha on 2008-12-25
Thanks all for the quick response, Nepherte seems to hit the problem on the head:

> **Nepherte said:**
> The user only has full access to his own user directory (/home/username). Anything else requires administrator (root) privileges. The root account on ubuntu is disabled by default, instead they use sudo.

I'm not particularly keen on having to do the sudo thing every time I want to go alter some directories on my external HD or save changes to a config file... if I have to I guess I'll have to, but first I need to ask the following two questions -

1) If the root account is disabled by default, "by default" implies it can be "re-abled"; is there a procedure to log in as root? On the install I checked 'log me in automatically', thinking this would effectively do that.

2) If being able to log in as root is just not a done thing, are there ways which allow my external HD to fall under my user account umbrella and for things like xampp to be installed in this area too? It sounds like this would amount to a similar end user experience as logging in as root, only just in the prescribed area.

Taurus -

I'd imagine the external HD is ntfs given I was using it with Windows and moved away as much as poss from fat32; I cannot format my USB keys to ntfs but the external HD probably has been if it didn't come like that (it's been a while since I started first loading it with data).

Like Arpanaut I've got some christmassy things to do so need to shift. Will be back tomorrow and will also give the "https://help.ubuntu.com/community/RootSudo" link some time too.

Cheers!

---

### Post by Jodha on 2008-12-25
> **Temposs said:**
> hello Jodha,
   I'm glad you've decided to try this lovely OS!

Now, as for your problem, 

...

I hope this is helpful!

Hi Temposs,

Yes that is helpful, on first look it sounds like faff though... given I've been windows based until recently and none of this is required in Windows -> files on my HD are there for me to move, delete, rename, whatever, without needing to do any weird stuff in a dos shell first.

If this is the only way, assuming there is no positive response to my last two questions, then I'll have to grab this bull by its horns. I'm not scared of the terminal window, its been quite fun here and there... just dont really want to be as bound to using it (and learning a load of new commands) as it seems as per the above advice.

Is there any moves in future to allow the o/s installer to log in as root, or is there some fact that I am not aware of which makes logging in as root a silly idea?

Anyway, that chrismassy stuff which is not taking place at my computer... cheerio for now :)

---

### Post by mkvnmtr on 2008-12-25
I think I read here that folk are not supposed to tell anyone how to log on as root. Or maybe it was something else. I had a little problem and loged on as root and it didn't help solve the problem. Besides I didn't have all the apps I had installed in my name. It't really not worth doing. I disabled after trying it for a few minutes. Sudo is better, at least I am thinking before each command.

---

### Post by Temposs on 2008-12-25
Jodha,
   If you would like to have easier graphical access to super user priveleges, then you may consider setting up a menu item for the file browser, which is called nautilus. You can for example right click on the main menu, and choose "Edit Menus". Then, perhaps choose "System Tools" under "Applications", then click the "New Item" button. Then you can create a launcher. In the Name field type: "Root File Browser". In the Command field type: "gksudo nautilus". You can choose an icon if you like. Now, you should have a new icon in your menu that will launch the file browser with administrator priveleges. You should try to only use this when you know you'll have to do something that requires root priveleges.

You may also want to check out the "Drag & Drop sudo" section of the [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) page that you've been pointed to previously.

Attempting to log in as root is not recommended or otherwise keeping root access constantly open. The security model of Ubuntu/GNU/Linux depends on users not having administrator access for most operations, and for those with administrator access to explicitly consent to administrative operations whenever one needs to be done, by typing in a password. If you wish to circumvent this security model, you are of course free to do so, but you do so at your own peril, and folks may not have as much sympathy for you if something does go wrong while you are circumventing the standard security checks that make Ubuntu rather nicely secure.

Hope you find this even more helpful ^_^

---

### Post by Nepherte on 2008-12-25
Logging in as root is indeed against the forum policies (look for a sticky topic in the security section). There is however a way to use your external hard disk as if it were yours. Therefore, you will have change something in /etc/fstab.

Open that file:
```
gksudo gedit /etc/fstab
```

Each entry in that file stands for a partition that gets mounted automatically on start up. You will have to find out whether your disk is already in there and if so which one it is. I suggest you post your /etc/ftab file in here and the output of the command
```
sudo fdisk -l
```

I can already tell you which options you have to add, but not where you have to add them. So hold on for now.

---

### Post by igknighted on 2008-12-25
Windows does in fact let you change any file on the hard drive (well, until Vista).  This also lets anyone, even random websites, arbitrarily run code on your system.  Sometimes without your knowledge.  A MAJOR (and I cannot emphasize that enough) security flaw.  Microsoft has been trying to fix this for years, but the issues are at the core of the OS.

The linux system was designed to be multi-user from the beginning.  It was meant to run on a central system and have many users log in as clients.  Obviously, you had to have a strict system of rights, so not just anyone could go changing system-wide files.  Thankfully, that security-oriented design comes in useful today by protecting the user from accidentally changing important files, and also keeps intruders from bringing your system down.

It really isn't too much of a hassle.  Go to getdeb.net and install the ubuntu-tweak program.  It has the option of turning on some "nautilus scripts", which include options to \"edit as root" (in the right click context menu).  This way you can have your security, without the need to open everything from the terminal.

As for your external drive... it is probably FAT32 (or vfat).  These drives have no permissions attached to them, so I am very curious why this would happen.  Perhaps you were browsing as root?  This could lead to root ownership of any files you create.  Try checking the drive on a windows install to see if you can access it, and that there are no errors on the drive.

---

### Post by Jodha on 2008-12-26
Hi All,

Thanks for all the info so far :) I guess there are a few details I need to get to grips with instead of thinking Ubuntu should work just like Windows, as it looks a little like Windows. I guess this is based on OS X from Mac where there I've not had these issues before either. Anyways -

As for Xampp and the config file, yes that worked and many thanks :)

Nautilus has been successfully added to the menu, but when I test it by trying to delete an un-needed file I get the same message that I do not have permission.

As for the chown command, am I right in assuming I should navigate the terminal so its sitting in the external HD root? Two issues...

- I cannot seem to navigate the terminal to this drive; I've "cd .." until I've gone as far back as possible, at each stage I've "dir"'ed and at no point have I seen the external HD appear in the directory listings. I seem to be able to go to the root of "filesystem" but this seems to only include files on the internal HD. In the graphical file browser the external HD appears as a separate area to "filesystem"

- If I try the "chown" command in any other place it tells me the external HD does not exist, which makes sense if its not appearing in the "dir" listings

The slightly annoying thing is; I've also got an Asus Eee with a strip-down version of a debian o/s which is not Ununtu. On this o/s I can use my external hd just as I can with a windows o/s.

Anyways, I can start web development now which is good  :)

As for the external... what if I back-up the data on the internal hd and format it under my user on Ubuntu?

---

### Post by shankhs on 2008-12-26
No problem Just go ahead(remember to backup ) setting permissions is very basic thing in linux and also the most beautiful thing,as a web-developer myself I find Linux to be more secure than windows due to the reasons igknighted pointed out.
Let me ask you one more question (since you were a windows user)
How would you format your external HD in linux???? :)
(google to get the answer)
P.S. When using Linux as a web-developer always remember one thing Google is GOD.

---

### Post by Moop on 2008-12-26
Ubuntu mounts external drives in the media directory. Look for it there. 

Check out the psychocats website in my sig and look at the file permissions and how to mount windows (ntfs) or mount linux (ext3). I'm sure that will help. 

In Synaptic Package manager you will find the packages nautilus-actions and nautilus-gksu. Installing those will give you a right click option to open any file with administration privileges (sudo). Use with care.

---

### Post by albinootje on 2008-12-26
> **Jodha said:**
>  All this time I have going through my head: "I should be telling you what to do, I installed the O/S, I am logged in as me, why do you not at least prompt for password like when installing software? This is stopping me from using this computer"

Can somebody tell me how to sort this out please? I cannot have my computer telling me what I can and cannot access/modify when it comes to my files here.


If you're the only user on your machine, then I can understand that you always want full and easy access of your files.

But if you want to develop pages for web-access, then you need to learn some more about permissions, but you don't want unknown intruders to break into your website in the future.

To make life a little easier for you, *and* to learn some more about computer-security in the meantime, check the manual pages of chmod and chown.
```

man chown
man chmod

```

See also : [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

