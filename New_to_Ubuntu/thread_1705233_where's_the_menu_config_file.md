---
title: "where's the menu config file?"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by Isaacgallegos on 2011-03-11
You know our applications main menu? There's a file that you can edit with gedit to better manipulate that menu. Any idea what that's called? I had to use it once and it's really fast for making big adjustments. 

Thanks!

---

### Post by MartyBuntu on 2011-03-11
Why not just right-click on the Applications tab and select **Edit Menus**? You can customize from there.

---

### Post by Isaacgallegos on 2011-03-12
I have a ton of wine apps I want to copy, not cut, over to other sections. It's less work just editing the file, rather than using the slow gui and manually making a new item one at a time, so I'll just wait until I find it or someone posts it. I'm in no rush.

---

### Post by Krytarik on 2011-03-12
System-wide menu items (desktop files) are stored in "/usr/share/applications".

User-specified ones are in "~/.local/share/applications".

If you change something in the first mentioned location, you have to update the menu item cache afterwards, otherwise the changes will get reverted at the next login:
```
rm /usr/share/applications/desktop.*.cache
sh -c "/usr/share/gnome-menus/update-gnome-menus-cache /usr/share/applications/ > /usr/share/applications/desktop.${LANG}.cache"

```Greetings.

---

### Post by Isaacgallegos on 2011-03-12
Oh wow! Is that the file that lets you run a command in the terminal? Thanks for the post. I don't see the text file I'm looking for but that's a handy directory! Thank you!

---

### Post by Isaacgallegos on 2011-03-12
Found it! Thanks all!
~/.config/menus/applications.menu

edit: 

Here's what you do:
Open applications.menu in your text editor of choice

then find the menu you want, like "Office".

You'll see
```

<Menu>
	<Name>Office</Name>
	<Include>
		<Filename>Dia Diagram Editor.desktop</Filename>
	
	</Include>
	
	
	<Exclude>
		<Filename>gnome-dictionary.desktop</Filename>
	</Exclude>
	<AppDir>/home/isaac/.local/share/applications</AppDir>
	<Exclude>
		<Filename>evolution.desktop</Filename>
	</Exclude>
</Menu>
```

Basically add these

```


		<Filename>wine-Programs-Microsoft Office-Microsoft Office Word 2007.desktop</Filename>
		<Filename>wine-Programs-Microsoft Office-Microsoft Office Excel 2007.desktop</Filename>
		<Filename>wine-Programs-Microsoft Office-Microsoft Office Access 2007.desktop</Filename>
		<Filename>wine-Programs-Microsoft Office-Microsoft Office PowerPoint 2007.desktop</Filename>

```
or any other wine app with in the <incldue> tags like this

I can just use this line of text "<Filename>wine-Programs-Microsoft Office-Microsoft Office ______ 2007.desktop</Filename>" and replace the "_____" with the application name, so this is really easy editing. The icon and everything is correct once I'm done. 

just a small note: I bought the whole suite from my University and it runs perfect out problems under wine. 

```

<Menu>
	<Name>Office</Name>
	<Include>
		<Filename>Dia Diagram Editor.desktop</Filename>
		<Filename>wine-Programs-Microsoft Office-Microsoft Office Word 2007.desktop</Filename>
		<Filename>wine-Programs-Microsoft Office-Microsoft Office Excel 2007.desktop</Filename>
		<Filename>wine-Programs-Microsoft Office-Microsoft Office Access 2007.desktop</Filename>
		<Filename>wine-Programs-Microsoft Office-Microsoft Office PowerPoint 2007.desktop</Filename>
	</Include>
	
	
	<Exclude>
		<Filename>gnome-dictionary.desktop</Filename>
	</Exclude>
	<AppDir>/home/isaac/.local/share/applications</AppDir>
	<Exclude>
		<Filename>evolution.desktop</Filename>
	</Exclude>
</Menu>

```
The effects are instant! You can separators and whatever you want. This file is very easy to play with. 

I might make a Python app that handles it better than the regular edit menu does, however, this file isn't hard to use.

In case anyone was wondering, I took these screenshots using $ gnome-screenshot --delay 10

---

### Post by Krytarik on 2011-03-12
Cool, I didn't know about those text files! I was already wondering how to *add* menu items manually, but so far I only needed to remove/modify user-specified items, and I've done it by removing/modifying their desktop-files in "~/.local/share/applications". Thanks for the info!

---

