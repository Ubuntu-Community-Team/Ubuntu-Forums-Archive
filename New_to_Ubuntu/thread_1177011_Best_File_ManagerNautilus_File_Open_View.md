---
title: "Best File Manager/Nautilus File Open View"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Andy06 on 2009-06-02
I am very happy with nautilus but it does have one or two problems. For example in whenever you want to open a file (specially an image/icon file for changing an icon or uploading or selecting images for wallpaper etc) you cannot see thumbnails, instead you only get list view with a preview of the selected file on the right pane.

Is there another file manager which fixes this? Any other file manager with more features? I am mainly looking for feature rich, lightness does not matter so much. 

Is this behaviour even a file manager thing though or is it just the way Ubuntu/Gnome works? What I mean is, is that window that pops up to select/open a file, a nautilus window? It looks a bit different, but then file selection pop ups do look different from the default view in all OSes.

---

### Post by Ms_Angel_D on 2009-06-02
Nevermind

---

### Post by Bradtek on 2009-06-03
Open nautilus
Click Edit / Preferences / Preview

Rest should be pretty self explanatory

> instead you only get list view with a preview of the selected file on the right pane.

I don't recall ever seeing a preview in a right pane ?

---

### Post by Andy06 on 2009-06-03
Ok many thanks!

By right pane, I meant right side. The default preview for when you try selecting a while through some other app is for it to show image previews on the right side.

---

### Post by Andy06 on 2009-06-03
Nope. Still doesn't make a difference. There are now small little icons right beside the text, about the height of the text itself. So that doesn't help much. Tried other views too.

Am I doing something wrong?

---

### Post by Andy06 on 2009-06-03
Ah I realised you just gave me advice for regular Nautilus windows. I was asking for "file open" windows and "select file" windows. You can see a sample by trying to change your desktop wallpaper. Then select add to select a picture from a folder and notice that the folder does not display proper thumbnails, just a sort of list view.

---

### Post by SuperSonic4 on 2009-06-03
> **Andy06 said:**
> I am very happy with nautilus but it does have one or two problems. For example in whenever you want to open a file (specially an image/icon file for changing an icon or uploading or selecting images for wallpaper etc) you cannot see thumbnails, instead you only get list view with a preview of the selected file on the right pane.

Is there another file manager which fixes this? Any other file manager with more features? I am mainly looking for feature rich, lightness does not matter so much. 

Is this behaviour even a file manager thing though or is it just the way Ubuntu/Gnome works? What I mean is, is that window that pops up to select/open a file, a nautilus window? It looks a bit different, but then file selection pop ups do look different from the default view in all OSes.

I like dolphin myself - it has a places menu on the left and a preview/info menu on the right and you can add a tree view if you like. Plus you can split the screen in 2 by pressing F3 and F4 for an embedded terminal. It's a strong KDE program so it could require a lot of deps

---

### Post by Andy06 on 2009-06-04
You know what really grinds my gears sometimes? The back button in nautilus is much narrower than the forward button. It should arguably be bigger. It is used more often and is just good UI design, see browsers as an example, when the buttons are not the same size, the back one is bigger.

Very small but annoying thing, any way to remedy it? I guess me using ultra dark themes which do not show borders unless you hover makes the issue worse.

---

### Post by Andy06 on 2009-06-11
Hey guys, 
Anyone have a solution yet? Would love picture thumbnails in file selection windows that open up. Its useless looking at alphanumeric names when what I want to select is a picture.

Also can the small back button be filed as a bug? ALL of the buttons are of standard width, only the BACK button (the most often used one) is a lot smaller than the rest. Faulty design?

Thanks a lot

---

### Post by mcduck on 2009-06-11
> **Andy06 said:**
> Hey guys, 
Anyone have a solution yet? Would love picture thumbnails in file selection windows that open up. Its useless looking at alphanumeric names when what I want to select is a picture.

Also can the small back button be filed as a bug? ALL of the buttons are of standard width, only the BACK button (the most often used one) is a lot smaller than the rest. Faulty design?

Thanks a lot

This really isn't a problem users can solve themselves.

The thing here is that the file selection dialog *does* have support for image previews, but the program that summons the file selection dialog has to tell if the preview should be enabled or not (as in many cases the preview part of the dialog would be useless and just waste the screen space. For example every time you use the dialog to browse any other than image files).

So, if you are using a program that uses GTK file selection dialog to select image files but doesn't have the preview enabled you should contact that program's developers and ask them to enable the preview.

I can't say anything about the back button in Nautilus. Seems to be just the same size as the other buttons so if it's smaller on your setup it must be because of the theme you are using..

edit: It just came to my mind that perhaps that happens if you have button texts enabled, and yes, it indeed seems that the back button is smaller in that configuration. Strange, and I agree that it should be at least the same size as other buttons. Although it would make no difference to me as I always disable text in toolbars anyway. :)

---

### Post by Andy06 on 2009-06-15
So its the app developer's fault? But pretty much EVERY single app then is faulty.

I think it would be much easier to solve it by just providing display controls in the GTK file selection window like there are in the normal nautilus window. Windows uses this to good effect. You can choose whatever settings you like for a particular app/folder and it tries to remember them.

1.I still am not sure if this GTK file selection windows is part of nautilus? Is it?

2.What exactly should I be doing to put in this request for a larger back button. Its a simple usability issue and a real no brainer but I don't want to get ripped on bugzilla for filing it as a bug when its more of a design bug than a functionality/operational bug.

---

### Post by Andy06 on 2009-06-16
Take Dolphin for example (or is it the QT file selection window?), I think it is indeed dolphin because it's file selection window looks a lot like it.
Anyway it does not matter which application summons it since the file selection window retains its adjustable settings - you can click on preview and then increase the thumbnail size to see thumbnails of pictures.
You cannot do this with Nautilus/GTK file selection window.

---

### Post by Andy06 on 2009-06-22
Hey guys can anyone please clear up whether that is a Nautilus window or a GTK generic file selection/save as window?

There are very new bug reports on this for the 'fix 100 bugs project for 9.10', so if this gets sorted quickly and there are enough users clicking the "this affects me" on launchpad, then it will be implemented in 9.10.

---

### Post by Andy06 on 2009-06-22
Also I filed a bug report in the same 100 bugs projects for 9.10 to fix the narrower back button. Check it out at launchpad:

[https://launchpad.net/hundredpapercuts](https://launchpad.net/hundredpapercuts)

---

