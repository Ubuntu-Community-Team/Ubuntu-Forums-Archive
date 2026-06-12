---
title: "UNity dash search home folder"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by gredawarha on 2011-04-30
Hi 

I am using Unity how can I search my home folder for items using the dash.

For example I have a PDF file called FRED saved in my document folder within my home folder.

If I run the dash and type FRED it does not come up, any way to get this to work?

Ta

---

### Post by Peter09 on 2011-04-30
if you do 

super+f and type Fred you should see your file .... may be its a bug in Unity

---

### Post by gredawarha on 2011-04-30
that does not seem to help, but thank you for trying.  I can select the dash and type firefoz and then select it and view the web but I cannot type any of my files and run them

---

### Post by aljazek on 2011-04-30
I guess super+f only see bookmarked folders (and not their content) and recently opened files.

---

### Post by gredawarha on 2011-05-01
The dash appears to allow you to search for folders but not individual files within the folders.

Surely there must be a way to do this?

---

### Post by vanadium on 2011-05-01
This is one thing I find does not work properly. The reason is that the fils search function is using Zeitgeist, a system that tracks what files you used. Indeed, only files you opened recently will appear there. Folders will not appear there, even if you just opened them: only documents appear under "Recent". They will appear under recent when you select "Folders" in the top right corner. 

- Thus, the quickest way to see and open a recently used folder is to right-click the file lens and select "Folders".
- To open a folder you know is there, you will need to open nautilus (Super+1) then find (Ctrl+F) the folder there.

---

### Post by hakermania on 2011-05-01
> **vanadium said:**
> This is one thing I find does not work properly. The reason is that the fils search function is using Zeitgeist, a system that tracks what files you used. Indeed, only files you opened recently will appear there. Folders will not appear there, even if you just opened them: only documents appear under "Recent". They will appear under recent when you select "Folders" in the top right corner. 

- Thus, the quickest way to see and open a recently used folder is to right-click the file lens and select "Folders".
- To open a folder you know is there, you will need to open nautilus (Super+1) then find (Ctrl+F) the folder there.

that's why I believe that searching by using windows key+F is the most useless thing in new ubuntu

---

### Post by Peter09 on 2011-05-01
Zeitgeist is not a simple search engine. It tracks your usage of files and when you do a search it returns results that are based on your usage. 

So if you aways open a file FRED and then a file BERT you will see both files returned from your search for FRED. I have not used it greatly yet but I suspect that the search results will get better as you use Unity.

---

### Post by vanadium on 2011-05-01
Point is indeed that you will only find files/folders that you actively used. At that point, it will be a quick way to find/open the files you are currently working with. It will not work to retrieve information from long time ago you know is there somewhere.

---

### Post by Peter09 on 2011-05-01
True, however for those who start afresh it will cover everything, its a matter of catching up.

---

### Post by GJCGJC on 2011-05-05
For me, the whole point of a file search is that you don't need to remember exactly where a file is - which is more likely if you haven't used it in a while. If it only searches recently used files it's undermining its own purpose, and I'm speaking as someone who generally really likes unity.

---

### Post by r-senior on 2011-05-05
It's poorly named as "Search Files and Folder" IMO. It should be "Search History" or similar. If you want to search for files, hit the Super key and type "Search". Then search for files. If you want to search for files often, pin "Search For Files" to the launcher.

---

### Post by dneff87 on 2011-05-05
This is somewhat ridiculous. I understand that the functionality of Zeitgeist is supposed to be fancy and intuitive, but in the process we've managed to deprive users of an obvious and simple basic search feature.

Gnome-Shell doesn't have this problem (though being so new it has many others).

Really, quite fundamentally, I should be able to press the super key and search any of my files. How recently I used them should not be a factor.

---

### Post by vanadium on 2011-05-06
> **GJCGJC said:**
> For me, the whole point of a file search is that you don't need to remember exactly where a file is - which is more likely if you haven't used it in a while. If it only searches recently used files it's undermining its own purpose, and I'm speaking as someone who generally really likes unity.

I couldn't agree more. There is an issue on lauchpad here [https://bugs.launchpad.net/ubuntu/+source/unity-place-files/+bug/646724](https://bugs.launchpad.net/ubuntu/+source/unity-place-files/+bug/646724) but I do not know to what it will lead, despite Mark himself being aware of the problem.

Gnome-do does this very nice. Why can't Unity?

---

### Post by r-senior on 2011-05-06
> **dneff87 said:**
> Gnome-Shell doesn't have this problem (though being so new it has many others).
What does Gnome Shell do for a file search?

---

### Post by vanadium on 2011-05-06
Probably, it finds, among other items, the file that you know is out there, when you type part of its name, independent of whether you have opened it recently or not.

---

