---
title: "How to change default application while opening programs"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-31
i have VLC player installed on my Ubuntu 8.10.. but whenever i want to open files(ie. i double click on a file to open it) it always gets opened in Totem movie Player..
Is there a way for me to change this to VLC, as we do in windows.. in windows we choose open with>> and select an application >> then check always use this application for these type of files..

Is there any such means here in Ubuntu.. if yes, please let me know.. thank you..

---

### Post by Gulyan on 2009-01-31
Right click a file and choose 'Properties'

Then you will see a tab named 'Open with'

---

### Post by chethankrish on 2009-01-31
thats what i do now.. but i dont want to do this action every time i want to open a file.. in windows i have an option to "use the same applicion for these types of files"

in wondows ,if i check the tab which says "use this applicion for these types of files" ..

say for example windows media player is the default player in windows.. if i want my mp3 to play in jet audio always instead of windows media player.. what i do is right click on any of my MP3s and select "open with" and there i can choose jet audio.. in the same "open with" window , i have an option to choose, which says " use this application for these types of files".. if i select that. then in future, all my MP3s gets opened in Jet audio.. 

now i want to know , if there is any such means in ubuntu...

---

### Post by labinnsw on 2009-01-31
You must have missed it. In properties, you can change the default application. This means by double clicking the file it will open with the new application each time.

---

### Post by Hobgoblin on 2009-01-31
Are you sure you are doing..

Right click
**Properties**
Open with

?

Right click > Open with, (the Windows way) is completely different.

---

### Post by labinnsw on 2009-01-31
Sorry Hobgoblin, I have correct that post

---

### Post by labinnsw on 2009-01-31
chethankrish

Don't right click and select "Open With"
Right click and select "Properties"
Then... select "Open With"

---

### Post by chethankrish on 2009-01-31
i am doing this.. but u r notunderstanding my question..My question is , i do not want to do this action every time i want to open a file.. for example an MP3 file.. i want to use VLC instead of totem player.. if i want to open a mp3 file using vlc player i have to right click on the file and select open with.. thats what i do.. but the question is, how do i make ubuntu remember my action.. ie whenever i double click on an mp3 file ,i want ubuntu to automatically open the mp3 file using VLC.. but thats not the case, because totem player is the default player , here in ubuntu..

---

### Post by chethankrish on 2009-01-31
hey thanks.. sorry for bothering you guys.. iused to right click and then select open with.. but when i select properties and then select open with.. its working.. thank you for your help...

---

### Post by labinnsw on 2009-01-31
Message deleted

---

### Post by Miwers on 2009-02-24
Hi,

Sorry for stealing this thread, but this might be relevant for OP too.

So, now that we established a way to change the default player for one specific filetype, I need to change the default player for ALL media files, without needing to right click every one and change properties.

There has to be a way to set VLC to be the default media player for all known media files.

Any1?

---

### Post by Flimm on 2009-02-24
Right-clicking on a file, clicking Properties, and then selecting the "Open With" tab will set the default for that file type. For example, if you do that with a .mov file, all .mov files from now on will open with the program you selected.
All you have to do now is repeat the same process once you come across a new file type or media format. As there are only about a dozen common media types, you'll soon have them all opening in your media player of choice in no time.

---

### Post by ikisham on 2009-02-24
Anyways, there is System>Preferences>Preferred Applications>Multimedia.

---

### Post by Miwers on 2009-02-24
Flimm:

I'd go nuts before I ever got through changing the default player for every media filetype that I have in my collection. That's why I want a solution that will work for ALL media filetypes, without the hassle of going through them all.

I'm sure, that the most common filetypes can be counted on two hands, but you have not seen my collection of various clips ;)

ikisham:

I have already done that, but that setting is apparently ignored by Ubuntu. This exactly the kind of solution I'm seeking, just like... working - but alas, it doesn't.

Any other suggestions?

---

### Post by unutbu on 2009-02-24
Edit this file:
~/.local/share/applications/mimeapps.list

It should look something like this:

```

[Added Associations]
image/jpeg=gqview.desktop;
video/mpeg=vlc.desktop;
video/x-flv=vlc.desktop;
video/mp4=vlc.desktop;
video/x-ms-wmv=vlc.desktop;
video/x-msvideo=vlc.desktop;
video/quicktime=vlc.desktop;
image/gif=gqview.desktop;
text/plain=emacsclient-emacs-snapshot.desktop;
```

Add a line for each mime/type you wish to handle. 
The "*.desktop" string you put on the right-hand side of the equals sign should refer to a file in /usr/share/applications/.

You may have to log out and log back in for the changes to become effective.

---

### Post by Miwers on 2009-02-24
unutbu:

Thank you - your post led me in the right direction.
I copied the /usr/share/applications/defaults.list to my home directory ~/.local/share/applications/defaults.list and edited it to only contain the mime-types referring to media, and altered it from the default (totem.desktop) to vlc.desktop.

That seemed to have solved the issue for me. There's about 50 different mime-types for media files, so I'm glad I won't have to manually change default player for those now :)

---

