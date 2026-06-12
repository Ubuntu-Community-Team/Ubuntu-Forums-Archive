---
title: "HOW TO: Make your own Chrome Themes"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by TheWarHawk on 2009-10-30
This tutorial is largely based off a tutorial I found at:
[http://kagashe.blogspot.com/2009/10/how-to-create-google-chrome-theme-with.html](http://kagashe.blogspot.com/2009/10/how-to-create-google-chrome-theme-with.html)

I decided to repost it and make it more clear.

First off download the ChromeTheme.tar

Extract all the files, and in the folder you should have 5 images in the image folder and a manifest.json

Editing your theme:
In the manifest.json you have a lot of options to edit, they'll be in RGB options, with a 4th number for transparency

The options are:
Name: Theme Name

Bookmark text: text color for you bookmarks

Frame: Color of the area behind your tabs

NTP_Background: Background color for new tab page(behind your picture)

NTP_Header: Mouseover color for new tab previews

NTP_Link: Link colors on new tab page

NTP_Section_Text: Text color under recently closed

NTP_Text: Text color on new tab page

Tab_Background_Text: Background tab text

Tab_Text: Foreground tab text

Toolbar: Toolbar color

With the images you can do whatever you like, I tried to get the resolutions right, but they could be a little off.


[IMG]http://yfrog.com/7btutsj[/IMG]

A - theme_ntp_background.png

B - theme_ntp_attribution.png

C - theme_frame.png 

D - theme_toolbar.png (best to use a pattern)

E - theme_tab_background.png (best to use a pattern)

Now all you have to do is go into chrome and go to 
Chrome://extensions/

And select the folder and it will create a .crx and a .pem file

Then go back into chrome and hit Ctrl+O and open the .crx file, hit save and there you go! :D

Hope everything's right, if not, post a correction por favor.

---

