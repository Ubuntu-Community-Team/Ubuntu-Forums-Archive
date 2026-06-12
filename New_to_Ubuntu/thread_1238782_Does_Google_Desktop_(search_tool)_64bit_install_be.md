---
title: "Does Google Desktop (search tool) 64bit install best from repos or from Google site?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by swarup on 2009-08-12
Has anyone used Google Desktop (the desktop search tool) for Ubuntu-- and in particular, 64bit Jaunty? Does it work well? I'd like to try it out. The [directions]("http://www.google.com/linuxrepositories/ubuntu704.html") for adding Google to the Ubuntu repos are for Feisty Faun however, so I didn't know whether the best would be to go with that set of directions, or instead to try the [direct download]("http://desktop.google.com/en/linux/download.html") from Google?

---

### Post by Schendje on 2009-08-12
I don't use it myself, but those instructions look like they'd be the same for 9.04. Repositories are always nice, because you don't have to update programs separately.

---

### Post by swarup on 2009-08-12
Yeah, you're probably right. And I guess it wouldn't add to the repo for my computer unless it were really the 64-bit Jaunty repo. So if it added at all, it would probably have to work. I could try that one.

---

### Post by swarup on 2009-08-25
I tried adding the Google desktop (i.e. desktop search program) to the Ubuntu repos for my computer, but it does not seem that Google has created this facility for Jaunty. I tried following the install instructions given on the above referenced site (for use with Feisty), and it went fine until the last step where one updates the repos, at which point I got an error message indicating there were no such repos for Jaunty. Anyone have any further news on this?

---

### Post by colin-m on 2009-08-30
I am fairly sure that Google does not offer a repo for Desktop Search any more. The deb installer for both 64 bit and 32 bit  versions are available here:- [http://desktop.google.com/en/linux/download.html](http://desktop.google.com/en/linux/download.html)

---

### Post by corncob on 2009-08-30
> **colin-m said:**
> I am fairly sure that Google does not offer a repo for Desktop Search any more. The deb installer for both 64 bit and 32 bit  versions are available here:- [http://desktop.google.com/en/linux/download.html](http://desktop.google.com/en/linux/download.html)

I went to the site and downloaded the appropriate deb file for my system (32 bit), installed it (I think -- didn't get any errors, said it was finished), and rebooted the computer.  What's it supposed to do?  I don't see anything different.

---

### Post by Ric_NYC on 2009-08-30
> **corncob said:**
> I went to the site and downloaded the appropriate deb file for my system (32 bit), installed it (I think -- didn't get any errors, said it was finished), and rebooted the computer.  What's it supposed to do?  I don't see anything different.

It is supposed to install an icon on your taskbar... near the volume control... It looks like an spiral.

---

### Post by mike555 on 2009-08-30
if Google search doesn't work for you you might try "Beagle" it's in the repos

---

### Post by colin-m on 2009-08-31
Go to 'Application->Google Desktop->Google Desktop' and check the options and then run it. You should see a spiral in your panel. If you go to 'Applications->Google Desktop->Google Desktop Preferences' to deselect any file types you don't want searched. Finally click on 'Save Preferences' This may help:-
 [http://desktop.google.com/linux/gettingstarted.html](http://desktop.google.com/linux/gettingstarted.html)

If 'Google Desktop' is not installed then it may have been downloaded to your desktop or home folder. If there is an icon on your desktop labelled'google-desktop-linux_current_i386.deb' (32 bit) or 'google-desktop-linux_current_amd64.deb' (64 bit) then double click the icon which will open a graphic installer. If it is not on your desktop, open the 'Places' menu and select 'Home Folder' and look for the google dektop icon. Double click the icon to install the application.

Hope this helps.

---

### Post by corncob on 2009-08-31
Thank you Ric, Mike, and Colin.  I see it now.

---

