---
title: "Wine wont show up PLEASE NEED HELP!"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by Scris101 on 2010-04-02
my wine folder wont show up under applications, it was getting too messy so i wanted to uninstall it. but when i installed it the programs still showed up so i went along to some websites telling me how to remove all of this stuff and after i typed all of these codes on terminal it basically reset my ubuntu but i have everything back now and i want to install wine again but after i did this i deleted the wine menu on applications and the program, i want wine back on the application menu but it wont show up ive tried right clicking and going to edit menu and theres nothing there can anyone please help me?

---

### Post by Chesamo on 2010-04-02
First off, punctuation is your friend.

That said, how did you reinstall WINE? Which repository did you grab it from? Where is the guide you used to edit your menu (afaik, you should *never* need to use the Terminal for simple menu operations)?

---

### Post by Scris101 on 2010-04-02
i uninstalled wine with ubuntu software center (im using 9.1) the reason why i used terminal is because there were the old program files, well files. it was just cluttering up space and it was really unorganized and i like, have a mild form of OCD. so i went online to look up how to uninstall those things. but now i want wine back so i reinstalled it with software center and the folder didnt show up under applications. So i right clicked it and went to "Edit Menus" thinking it was just unchecked. But when i went into it the folder wasnt even there, i dont know what happened.

---

### Post by Calash on 2010-04-02
What happens when you go to the terminal and type the following


wine --version

---

### Post by Chesamo on 2010-04-02
1. It's 9.10. 9 for 2009 and 10 for October.
2. What program files? The Ubuntu programs or the WINE program files?
3. If you don't have any WINE programs installed (or programs you can re-install later), try this: ```
$ sudo apt-get purge wine
$ cd ~/ && rm -r .wine/
$ sudo apt-get install wine
```
It will completely wipe out the WINE configuration and reinstall WINE. Worst comes to worst, you can create menu items yourself.

---

### Post by Scris101 on 2010-04-02
> **Calash said:**
> What happens when you go to the terminal and type the following


wine --version

evan@evan-desktop:~$ wine --version
wine-1.0.1

---

### Post by Scris101 on 2010-04-02
> **Chesamo said:**
> 1. It's 9.10. 9 for 2009 and 10 for October.
2. What program files? The Ubuntu programs or the WINE program files?
3. If you don't have any WINE programs installed (or programs you can re-install later), try this: ```
$ sudo apt-get purge wine
$ cd ~/ && rm -r .wine/
$ sudo apt-get install wine
```It will completely wipe out the WINE configuration and reinstall WINE. Worst comes to worst, you can create menu items yourself.'

the wine program files, and ill try the code now

---

### Post by Scris101 on 2010-04-02
> **Chesamo said:**
> 1. It's 9.10. 9 for 2009 and 10 for October.
2. What program files? The Ubuntu programs or the WINE program files?
3. If you don't have any WINE programs installed (or programs you can re-install later), try this: ```
$ sudo apt-get purge wine
$ cd ~/ && rm -r .wine/
$ sudo apt-get install wine
```It will completely wipe out the WINE configuration and reinstall WINE. Worst comes to worst, you can create menu items yourself.

grrr the code isnt working everything is right and it accepcts everything but its still not showing up on my menu

---

### Post by Chesamo on 2010-04-02
> **Scris101 said:**
> the wine program files
...You shouldn't need Terminal commands to uninstall programs that are installed under WINE... I wasn't even aware that that was possible >_>

Also, don't triple-post. There's an EDIT button in the bottom right-hand corner of your post. You can append using that.

Okay, to create your own WINE menu, you can do this:

1. Open up the menu editing utility
2. Create a folder called "WINE"
3. Inside that, create a Launcher called "Configure WINE" with the command "winecfg"
4. Also, create a Launcher called "Browse C: Drive" with the command "nautilus /home/evan/.wine/drive_c/"
5. Create a folder called "Programs"
6. Inside that, create launchers individually with the following attributes:
* Named the name of your program
** Command: ```
env WINEPREFIX="/home/evan/.wine" wine "C:\Program Files\PROGRAM_PATH"
```

---

### Post by Scris101 on 2010-04-02
Sorry, i wasnt trying to delete the programs i should of used better words. when i opened my C drive (wines c drive) i deleted all of the program's files but when i went to the wine folder under applications the icons and folders for those programs were still there and i wanted to get rid of them because they were no longer needed, idk what i did after that.

---

### Post by Calash on 2010-04-02
At least we know wine is in and working.


What is the output of the following?
cat ~/.config/menus/applications.menu


With this we are looking for a Wine entry that is followed by a </Deleted> tag.

---

### Post by Chesamo on 2010-04-02
> **Calash said:**
> With this we are looking for a Wine entry that is followed by a **<Deleted/>** tag.
Fixed.

Also, why didn't I think of that? @_@ Geez, I'm off today.

---

### Post by Scris101 on 2010-04-02
> **Calash said:**
> At least we know wine is in and working.


What is the output of the following?
cat ~/.config/menus/applications.menu


With this we are looking for a Wine entry that is followed by a </Deleted> tag.
if im suposed to type this in teminal it says 

cat: /home/evan/.config/menues/applications.menu: No such file or directory

---

### Post by Chesamo on 2010-04-02
You misspelled "menus".

---

### Post by Scris101 on 2010-04-02
OHHH ok haha im so dumb this is what it says 

<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
    <Name>Applications</Name>
    <MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
    <Menu>
        <Name>wine-wine</Name>
        <Deleted/>
    </Menu>
    <Menu>
        <Name>System</Name>
        <DirectoryDir>/home/evan/.local/share/desktop-directories</DirectoryDir>
    </Menu>
    <Menu>
        <Name>Other</Name>
        <DirectoryDir>/home/evan/.local/share/desktop-directories</DirectoryDir>
    </Menu>
    <DefaultLayout inline="false"/>
    <Menu>
        <Name>alacarte-made</Name>
        <Directory>alacarte-made.directory</Directory>
        <Deleted/>
    </Menu>
</Menu>

---

### Post by Chesamo on 2010-04-02
> [b]<Menu>
<Name>wine-wine</Name>
<Deleted/>
</Menu>[/b]
Remove the <Deleted/> tag and it *should* restore the folder.

It looks a little empty though...

---

### Post by Calash on 2010-04-02
There it is :)


Type gedit ~/.config/menus/applications.menu


Scroll down to the following lines

```

<Menu>
<Name>wine-wine</Name>
<Deleted/>
</Menu>

```

Delete the line that says <Deleted/>  (Thanks for catching my typo earlier Chesamo :) )

Save the file and take a look.  You may have to log out and back in...I do not remember if Gnome updates on the fly or not.


Edit:  Beat me to it.  I think it is empty because it should be pulling the application list from a different file.  I will have to look into that when I get a chance.

---

### Post by Chesamo on 2010-04-02
> **Calash said:**
> Edit:  Beat me to it.  I think it is empty because it should be pulling the application list from a different file.  I will have to look into that when I get a chance.
Shazam, ninja-post! ;-)

Also, I took a look at mine and it was populated thusly: ```
	<Menu>
<Name>wine-wine</Name>
<Menu>
<Name>wine-Programs</Name>
<Exclude>
<Filename>wine-Programs-FileMaker Pro.desktop</Filename>
</Exclude>
<AppDir>/home/tony/.local/share/applications</AppDir>
<Exclude>
<Filename>wine-Programs-Apple Software Update.desktop</Filename>
</Exclude>
<Menu>
<Name>wine-Programs-Accessories</Name>
<Exclude>
<Filename>wine-notepad.desktop</Filename>
</Exclude>
<AppDir>/home/tony/.local/share/applications</AppDir>
</Menu>
<Menu>
<Name>wine-Programs-Bonjour</Name>
<Exclude>
<Filename>wine-Programs-Bonjour-Bonjour Printer Wizard.desktop</Filename>
</Exclude>
<AppDir>/home/tony/.local/share/applications</AppDir>
<Exclude>
<Filename>wine-Programs-Bonjour-About Bonjour.desktop</Filename>
</Exclude>
</Menu>
</Menu>
<AppDir>/home/tony/.local/share/applications</AppDir>
<Exclude>
<Filename>wine-uninstaller.desktop</Filename>
</Exclude>
<Exclude>
<Filename>wine-browsedrive.desktop</Filename>
</Exclude>
<Exclude>
Filename>wine-winecfg.desktop</Filename>
</Exclude>
<Deleted/>
</Menu>
```
So, I've both hidden and deleted my WINE folder. Yours is pretty empty, so I don't know...

---

### Post by Scris101 on 2010-04-02
OMG OMG YES YES YES!!! THANK YOU BOTH SO MUCH!!!!! YES!!!! i will now dedicate my life to finding you 2 and giving you both a billion dollars! Yes! thank you so much it worked!

---

### Post by Chesamo on 2010-04-02
Easy there, killer. Mark the thread solved and that's thanks enough for me ;-)

---

