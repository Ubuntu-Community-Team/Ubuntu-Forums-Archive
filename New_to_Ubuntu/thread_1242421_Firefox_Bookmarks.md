---
title: "Firefox Bookmarks"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by johnexpgn on 2009-08-17
I am wanting to copy my Firefox Bookmarks in windows to Firefox Bookmarks in ubuntu.
Can I just copy the profile/bookmarks.html file in the windows version and paste it into the ubuntu version (having deleted the original first)?

---

### Post by realzippy on 2009-08-17
Yes.

---

### Post by arochester on 2009-08-17
You could use the Firefox extension called XMarks. Install it on Windows. Send your bookmarks to a server in cyberspace. Install it on Linux. Access the server in cyberspace and download the same bookmarks.

That way you can have the same bookmarks on several computers - Windows, Linux, Mac. An update on one machine is synched across all.

---

### Post by ajgreeny on 2009-08-17
You can also just backup your bookmarks using the Organise bookmarks item in the bookmarks menu.  Save it as a json or html file and take that to the new machine.  If you have not actually backed up bookmarks to an html file manually, that file will not be the up to date version of your bookmarks since FF3 does not use that file as the default any more.

---

### Post by lovinglinux on 2009-08-17
> **johnexpgn said:**
> I am wanting to copy my Firefox Bookmarks in windows to Firefox Bookmarks in ubuntu.
Can I just copy the profile/bookmarks.html file in the windows version and paste it into the ubuntu version (having deleted the original first)?

That file does not contain your bookmarks. It contains the default bookmarks that you see when you create a new profile. You need to copy the file **places.sqlite**, which is the database where your bookmarks are stored.

Take a look at the Backup section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) for other options.

---

### Post by harry2006 on 2009-08-17
without getting into any hassale, I'ld suggest using some bookmark sync tool/plugin, there are many e.g deli.cio.us, Xmarks etc[use google to get more]...I've been using Xmarks/Foxmarks for last 4 yrs..and its really wonderful..thank you.

---

### Post by stalkingwolf on 2009-08-17
try manage bookmarks, import restore, export html

---

### Post by Paddy Landau on 2009-08-17
> **arochester said:**
> XMarks...
+1 for [Xmarks]("https://addons.mozilla.org/en-US/firefox/addon/2410"). It works brilliantly.

---

### Post by johnexpgn on 2009-08-18
The Xmarks idea sounds wonderful. As I am only a beginner with this could someone help a with a bit more practical detail?
I downloaded the Xmarks add on from the link on to the linux firefox 3 browser. Do I have to do the same on the windows firefox browser and then magically somehow they interrelate? Or do I have to do something else?

---

### Post by zeroseven0183 on 2009-08-18
> **stalkingwolf said:**
> try manage bookmarks, import restore, export html

I think this is one of the easiest way to copy your bookmarks. Export all of it to an HTML file in Windows then import it in Ubuntu.

Bookmarks > Organize Bookmarks > Import and Backup >
 a. Export HTML
 b. Import HTML

---

### Post by Paddy Landau on 2009-08-18
> **johnexpgn said:**
> As I am only a beginner with this could someone help a with a bit more practical detail?
Add Xmarks on to every computer that you wish to synchronise (I have three computers that I keep synchronised with each other).

Follow the instructions in the Add-on's Preferences.

[LIST]
[*]Start with the computer that already has the bookmarks and passwords that you need. You'll create an account and upload your bookmarks and passwords to the Xmarks server (Xmarks does it all for you).
[*]Then go on to any other computer where you want to pull in the bookmarks and passwords. You'll sign in and download the details from the Xmarks server.
[/LIST]
Thereafter, Xmarks will 'magically' synchronise your bookmarks and passwords every time you go onto each computer.

---

### Post by johnexpgn on 2009-08-18
Thanks Paddy Landau & zeroseven0183!

Your suggestion doing an import / export with the html bu worked first time.

I also know more about Xmarks and how to use it.

Thread is now resolved!

---

