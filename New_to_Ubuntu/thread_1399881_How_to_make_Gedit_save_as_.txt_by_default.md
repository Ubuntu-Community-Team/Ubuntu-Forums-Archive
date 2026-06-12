---
title: "How to make Gedit save as .txt by default"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by singaporexuexi on 2010-02-06
Hello there!
I have been using Gedit for a while now, but can't figure out how to get it how to save by default as a text file (.txt) like notepad does in Windows. I don't like the fact that Gedit by default does not save in any file extension. Any help with this is appreciated.

:guitar:

---

### Post by kaivalagi on 2010-02-06
> **singaporexuexi said:**
> Hello there!
I have been using Gedit for a while now, but can't figure out how to get it how to save by default as a text file (.txt) like notepad does in Windows. I don't like the fact that Gedit by default does not save in any file extension. Any help with this is appreciated.

:guitar:

Just type the file name with a ".txt" on the end :)

Seriously though I don't think you can, you define the extension by virtue of the filename given...I mean how many extensions are there for files which all ultimately contain text quite a few...

---

### Post by coffeecat on 2010-02-06
> **singaporexuexi said:**
> I don't like the fact that Gedit by default does not save in any file extension.

I can appreciate your frustration, but I think you may be conditioned by using Windows. Linux (usually) doesn't need filename extensions to define the type of file, unlike Windows which does. The filetype is defined in metadata in the file header. This is why Gedit doesn't add any extension by default. Save a plain text file in Linux without a .txt extension, double-click on it and it will open in gedit (or the default text editor). Try to open it in Windows, and Windows will ask you which app to open it with because it can't identify the file type without the extension. This is a limitation of Windows.

Try this experiment. Rename a JPEG image from "filename.jpg" to "filename". In Ubuntu, right-click on it and select 'Properties'. It shows as Type JPEG Image, doesn't it? Now double-click on it. It opens in EoG, doesn't it? Now try that with the same extensionless JPEG in Windows. Interesting, yes?

In fact Linux will utilise a file extension if it's there, but in most cases it doesn't need them. So - if you need to be able to open your gedit-saved text files in Windows, you need to add .txt manually to the filename. If you don't, then you don't need an extension. Simple.

---

### Post by singaporexuexi on 2010-02-06
I know that you just type .txt on the end. I have programmed in Java, C++, and HTML and in those languages you have .java, .cpp, and .html files. It is easy to do that. I just want to be able to have the default setting in Gedit to save as a text file instead of no extension.

---

### Post by coffeecat on 2010-02-06
> **singaporexuexi said:**
>  I have programmed in Java, C++, and HTML 

Fair enough, but you've posted in the Absolute Beginners' section. Absolute beginners don't usually have such experience.

---

### Post by kaivalagi on 2010-02-06
> **singaporexuexi said:**
> I know that you just type .txt on the end. I have programmed in Java, C++, and HTML and in those languages you have .java, .cpp, and .html files. It is easy to do that. I just want to be able to have the default setting in Gedit to save as a text file instead of no extension.

I understand you, defaulting to .txt when no file exists yet would make some sort of sense...especially coming from a windows background where extensions mean so much and are expected.

However, the same argument could potentially be made for no extension if you were coming from another background and getting annoyed with .txt everywhere...

As coffeecat has mentioned file types are handled differently from windows and so the extensions are not as important for the system to know what to do.

If you save a text file without extension it will open in your default editor on double click...so not so important

If you feel that strongly about it make a feature request for gedit with it's developer(s) and argue your case.

---

### Post by Girya on 2010-02-06
> **singaporexuexi said:**
> Hello there!
I have been using Gedit for a while now, but can't figure out how to get it how to save by default as a text file (.txt) like notepad does in Windows. I don't like the fact that Gedit by default does not save in any file extension. Any help with this is appreciated.

:guitar:

**hack alert:**

interesting challenge. How I solved it.

1. write a shell script and save it in your bin directory:

```
#!/bin/bash
cd ~/gedit
gedit
``` 

```
chmod +x name_of_shell_script.sh
```


```
mkdir ~/gedit
```

edit gedit launcher:

right click Applications menu > Edit Menus

click on accesories gedit properties

change gedit %U to /home/username/bin/name_of_shell_script.sh

now when you save a file it will save to gedit directory by default. 

write a sed script that changes all files in gedit directory to have .txt extensions. and set it as a cron job.

I warned you this was a hack!

---

### Post by Morbius1 on 2010-02-06
If you're using gnome:

Open up gedit
Immediately save it as gedit.txt to **/home/username/Templates**

*If you don't have a Templates folder, create one but don't forget to keep the first "T" as caps.*

Now Right click an empty space on your Desktop > Create Document > gedit

It will open up gedit to gedit.txt. [COLOR=Blue]EDIT: That's not quite accurate. It will place a gedit.txt file on your desktop. You'll have to double click it to open gedit.[/COLOR] After you edit the file and click "Save As" only the filename will be highlighted, not the txt file extension.

BTW you can put just about anything in that Templates folder like open office templates and such.

---

