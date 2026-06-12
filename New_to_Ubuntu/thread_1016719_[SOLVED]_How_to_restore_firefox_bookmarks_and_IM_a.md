---
title: "[SOLVED] How to restore firefox bookmarks and IM after new distro upgrade"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by MooseMagnet on 2008-12-20
I backed up all I need. And restored all my applications.

I have all applications, etc. Except my firefox bookmarks and instant messenger data.

I got all my Skype information, contact list, etc.

But not firefox bookmarks and no instant messenger data.

How can I restore the firefox bookmarks?
How can I restore the instant messenger data (buddy list)? 

I backed up and restored these:  /etc, /usr, /var, and /rich (home folder)

Thanks

---

### Post by imag1narynumber on 2008-12-20
> **MooseMagnet said:**
> I backed up all I need. And restored all my applications.

I have all applications, etc. Except my firefox bookmarks and instant messenger data.

I got all my Skype information, contact list, etc.

But not firefox bookmarks and no instant messenger data.

How can I restore the firefox bookmarks?
How can I restore the instant messenger data (buddy list)? 

I backed up and restored these:  /etc, /usr, /var, and /rich (home folder)

Thanks

You should have a ~/.mozilla folder that contains your profile and config files.  I don't use an IM, so I don't know about that.  There's a page I used from the Mozilla site.  I can't find that one, but this one seems to contain all the relevant information.

[http://support.mozilla.com/en-US/kb/Recovering+important+data+from+an+old+profile](http://support.mozilla.com/en-US/kb/Recovering+important+data+from+an+old+profile)

---

### Post by imag1narynumber on 2008-12-20
Wouldn't you know it, I just found the other link.

[http://support.mozilla.com/en-US/kb/Backing+up+your+information](http://support.mozilla.com/en-US/kb/Backing+up+your+information)

---

### Post by abn91c on 2008-12-20
> **imag1narynumber said:**
> You should have a ~/.mozilla folder that contains your profile and config files.  I don't use an IM, so I don't know about that.  There's a page I used from the Mozilla site.  I can't find that one, but this one seems to contain all the relevant information.

[http://support.mozilla.com/en-US/kb/Recovering+important+data+from+an+old+profile](http://support.mozilla.com/en-US/kb/Recovering+important+data+from+an+old+profile)
go to the above mentioned folder, the bookmarks are in a file named [COLOR="Blue"]**bookmarks.html**[/COLOR]

---

### Post by BDNiner on 2008-12-20
The bookmarks.html file contains all your bookmarks. You also use the add on foxmarks for firefox that stores your bookmarks on their server and allows u to share them accross multiple computers.

The buddy lists are maintained by the service that you use for IM. so you should just have to log in with your AIM, MSN...etc account and the buddy list will show up.

---

### Post by MooseMagnet on 2008-12-20
Thank you much.

---

### Post by MooseMagnet on 2008-12-20
I suspect I've typed the rysnc command incorrectly when I restored.

I did this:

sudo rsync -avz /media/USB/12_19_2008/rich /home/rich

I backed up /rich to the folder "12_19_2008" on the external USB. But I think maybe when I issued this command, it restored to an incorrect location.

Does this command look wrong to you?

---

### Post by shalomhk on 2008-12-20
An alternative to manipulating these files is by using "Foxmarks", a Firefox addon.

This small applet saves all your bookmarks (on the tool bar, the pull-down menu, folders and subfolders...) to a remote server. All you need to do is to either download the foxmarks add-on to automatically sync your new PC (or PC at work/school) with your new bookmarks OR you can go to a website URL they provide you that consists of URL links of your bookmarks.:P

---

### Post by anjilslaire on 2008-12-20
If you use pidgin, just back up your ~/.purple directory, just like your /.mozilla folder.

---

### Post by MooseMagnet on 2008-12-20
I copied bookmarks.html from the USB drive, and pasted into etc/firefox/profile   but it didn't work. 

I don't know anything about pidgeon, or the other suggestions.

This is too weird. Where did my bookmarks go?

What am I doing wrong?

---

### Post by abn91c on 2008-12-20
> **MooseMagnet said:**
> I copied bookmarks.html from the USB drive, and pasted into etc/firefox/profile   but it didn't work. 

I don't know anything about pidgeon, or the other suggestions.

This is too weird. Where did my bookmarks go?

What am I doing wrong?
open firefox go to bookmarks>organize bookmarks>import and back up>import html then go to the usb and select bookmarks.html

---

### Post by MooseMagnet on 2008-12-20
That did not work.

It just added duplicate basic categories:
Get Bookmark Add-ons
Bookmarks Toolbar Folder
Ubuntu and Free Software Links
etc.....

But did not restore bookmarks.
I even grabbed bookmarks from a backup I did six months ago. 

Something is very wrong here.

---

### Post by abn91c on 2008-12-20
not sure what happened but just to double check expand all the categories and look around to make sure it was not renamed something like "from Mozilla" or something like that.
That was the method I used to copy my bookmarks when I reinstalled ubuntu  and copied that file from my other kubuntu desktop

---

### Post by BDNiner on 2008-12-20
Wait is everything gone, even your history does not work anymore? I had a similar issue two days ago and it turn out that the profile is corrupted.

---

### Post by mc4man on 2008-12-20
> I even grabbed bookmarks from a backup I did six months ago.

Are you getting the backup from the same import -> browse to .mozilla/firefox/xxxxxx.default -> bookmarkbackups folder and choosing the latest xx.html

---

### Post by MooseMagnet on 2008-12-20
I displayed hidden files in /home on the USB
Copied bookmarks.html from /.mozilla/firefox/...
Then pasted into /home/rich/.mozilla/firefox/... on laptop
Then used the gui in Firefox to do this:
Bookmarks > Organize Bookmarks > File > Import

And imported bookmarks.html from /home/rich/.mozilla/firefox/profile...

I have restored the bookmarks thank you.

Now I need to get the microphone back, and figure out what's wrong with the internet security settings.

---

### Post by anjilslaire on 2008-12-20
<disregard>

---

### Post by kansasnoob on 2008-12-20
Well, you did your backup a lot different than I do mine but in your backup if you can find your home > show hidden > .mozilla > firefox > 8random#.default > places.sqlite that is your bookmarks. to repeat; places.sqlite is your bookmarks, so if you copy-n-paste it to your current 8random#.default you should have your bookmarks back.

If you used a CD you'll likely have to restore read & write permissions.

BTW, when I say "8random#.default" it's just that. Eight random figures - dot - default!

---

### Post by presence1960 on 2008-12-20
I have been using my firefox and thunderbird profile for a few years now. I have never had to start over or create a new profile. I always keep a copy of both profile folders on a usb drive for safekeeping. If I ever need them again I just copy the Firefox profile folder into the /home/user/.mozilla/firefox folder. Then open a terminal window and type "sudo firefox -profilemanager"  This will open the profile manager which gives you the option to create and delete profiles and to choose which profile folder you wish to use. **DO NOT delete the default profile until you have created another or you will have some trouble. ** I create a new profile then click choose folder and choose the profile folder I just placed in the .mozilla/firefox folder. I then delete the profile Firefox created when installed. it is also safe to then delete that profile's files. Works the same with Thunderbird except the thunderbird profile folder is in /home/user/.mozilla-thunderbird folder. This works great I have been using the same profile for years which came from Windows. In Windows you can do the same thing by pasting your profile folder into the proper folder whose location will vary depending on your version of windows. Then use the run command and type "firefox.exe -profilemanager" to open the profile manager. Just remember to back up your profile folder every so often so it is up to date in case something happens. To do the same to thunderbird just substitute thunderbird in the above commands for Linux or windows.

---

