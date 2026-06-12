---
title: "Where do you save files to?"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by JREAM on 2009-11-14
I am wondering the best way to do this please.
Linux has **home/user**
Is that equivalent to [B]c:/documents and settings/user

[/B]So I am wondering, should I save all my files in the home/user area?
If I have a bunch of project files I should organize it all in there?

My only reason for asking this is because if you do** view hidden files** in the home/user you get a lot of folders. So I would like to know the most common place people save things.

Also, is there a way to change the location where things are automatically downloaded to?
And, is there a way to make a hotkey, like Super(WinKey) + E open the Natulus File Browser?

---

### Post by SuperSonic4 on 2009-11-14
I save mine on the desktop.

It's wise to save it anywhere in /home/user really as that's all your user owns on the system

---

### Post by JREAM on 2009-11-14
> **SuperSonic4 said:**
> I save mine on the desktop.

It's wise to save it anywhere in /home/user really as that's all your user owns on the system

Thank you this is what I was curious about, that was a fast reply by the way lol

---

### Post by bacardiandwatermelon on 2009-11-14
To show hidden files it is "ctrl + h". Under System->Preferences->Keyboard Shortcuts->Desktop->Home folder can be set to "windows + e".

---

### Post by marcopolo1981 on 2009-11-14
For the record, if you un-hide all files in a windows install, the users home directory has about the same number of files and folders as the Ubuntu home/user directory. Windows is just a bit more secretive and hides them better.:p
Just a useless bit of trivia

---

### Post by coffeecat on 2009-11-14
> **JREAM said:**
> So I am wondering, should I save all my files in the home/user area?
If I have a bunch of project files I should organize it all in there?

Yes, yes and yes. /home/user is for your personal files. You'll run into permissions problems elsewhere anyway.

Just set up folders (Videos, Music, Documents, whatever you want) in there the way you want. If you go to Places > Home Folder, you'll see that your desktop is the first folder there. It may have a special icon, but it's just another folder. (Just like in Windows; just like in MacOS.)

---

### Post by SuperSonic4 on 2009-11-15
You *can* put them on a separate partition and then add an entry in fstab so thye mount on boot but it is trickier in comparison

---

### Post by mr clark25 on 2009-11-15
i don't know about everone else, but i told my computer to put all downloads in a folder titled "downloads" in my documents folder. that seems to be best...

---

### Post by J-Buntu on 2009-11-15
Currently my Home folder contains - Accounts, Messenger Received, Crash Logs, Desktop, Documents, Downloads, Karmic Sources, Music, Notes, P2P, Pictures, Themes, Torrents, Videos.

---

### Post by halitech on 2009-11-15
> **mr clark25 said:**
> i don't know about everone else, but i told my computer to put all downloads in a folder titled "downloads" in my documents folder. that seems to be best...

+1 but I created the downloads folder in ~/ instead.

---

### Post by Paqman on 2009-11-15
Your home folder is intended to be the place for any files you want to dump. Personally I put all my important stuff on a network share that has some redundancy. I only use home for unimportant things like wallpapers or temporary storage. 

Anything I need access to when away from home goes into UbuntuOne. I also have a daily anacron job that backs UbuntuOne up onto the same redundant storage mentioned above.

---

### Post by kgroll on 2009-11-15
In my opinion, the **/home/<user>** most closely resembles the Windows **C:/Documents and Settings/<user>/My Documents** directory.  I prefer to save all of my work in this area, or an appropriately labeled subdirectory, principally because this is the starting point for terminal navigation.  You might consider creating a directory /home/<user>/workspace for your projects.

Regarding download location -
I assume you are talking about files downloaded from within your browser.  If you're using firefox, you can change this location in Edit>Preferences>Save Files to: (Browse...).

I'm sure there's an answer to your hotkey assignment question, unfortunately I don't have it.  But in the meantime, you could use the 'Run Application' shortcut: Alt+F2. Then just start typing Nautilus and it should autocomplete (maybe not the first time?).  Not very elegant, but at least you can keep your hands on the keyboard.

---

