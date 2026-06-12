---
title: "&quot;chrome&quot; folder mozilla?"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by WubiAR on 2011-07-07
Hello,

I recently converted from Windows 7 to Ubuntu. I was trying to implement a text wrap feature on Firefox, so when I zoom into webpages to read, I wouldn't have to trail all the way with my horizontal slider bar. 

I had begun following this method here: [http://ttcs.wordpress.com/2008/02/12/how-to-apply-word-wrap-to-text-files-viewed-in-mozilla-firefox/](http://ttcs.wordpress.com/2008/02/12/how-to-apply-word-wrap-to-text-files-viewed-in-mozilla-firefox/), which then led me to the Mozilla website, and there I found out the location of the hidden .mozilla folder. So then I followed this Ubuntu user tutorial [http://blog.websitestyle.com/index.php/2007/01/13/how-to-customize-firefox-userchrome-on-ubuntu/](http://blog.websitestyle.com/index.php/2007/01/13/how-to-customize-firefox-userchrome-on-ubuntu/) to find out how to manipulate the .css file in this OS.  However, when I got to my .default folder, I realized that there is no "chrome" folder. The issue here is that the tutorial I was following from that blog only works with a file contained within that "chrome" folder, called "userChrome-example.css". 

What happened to the "chrome" folder and its contents? Is there any other web browser that supports text wrapping? I tried installing the corresponding firefox add-on, but it didn't work.

---

### Post by dniMretsaM on 2011-07-07
If you open the userChrome-example.css file and read the instructions you'd see what you're missing.

---

### Post by WubiAR on 2011-07-07
I don't have that file in my .mozilla folder.

---

### Post by Alwimo on 2011-07-07
Hmmm. I don't have it either, in Firefox 5, but I had it in the past.

Perhaps Firefox 5 no longer has it?

---

### Post by WubiAR on 2011-07-07
Shoot... So is there any other way of **wrapping your text in the browser**? I find it a burden to move the slider over to read text, especially when zoomed in.

---

### Post by lovinglinux on 2011-07-07
Just create the folder and the file, then edit it accordingly.

You can also use [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/2108/") extension to manipulate css style sheets.

---

### Post by WubiAR on 2011-07-07
> **lovinglinux said:**
> Just create the folder and the file, then edit it accordingly.

You can also use [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/2108/") extension to manipulate css style sheets.

I wish it would be that easy for me to do that. Is it simply just making the folder, creating a blank .css file and following the instructions from the guy's tutorial here? [http://ttcs.wordpress.com/2008/02/12/how-to-apply-word-wrap-to-text-files-viewed-in-mozilla-firefox/](http://ttcs.wordpress.com/2008/02/12/how-to-apply-word-wrap-to-text-files-viewed-in-mozilla-firefox/)

If you don't mind, could you show me step-by-step as to what I have to do? :(

---

### Post by lovinglinux on 2011-07-07
> **WubiAR said:**
> I wish it would be that easy for me to do that. Is it simply just making the folder, creating a blank .css file and following the instructions from the guy's tutorial here? [http://ttcs.wordpress.com/2008/02/12/how-to-apply-word-wrap-to-text-files-viewed-in-mozilla-firefox/](http://ttcs.wordpress.com/2008/02/12/how-to-apply-word-wrap-to-text-files-viewed-in-mozilla-firefox/)

If you don't mind, could you show me step-by-step as to what I have to do? :(

Yes. Let me know if it doesn't work.

---

### Post by WubiAR on 2011-07-07
> **lovinglinux said:**
> Yes. Let me know if it doesn't work.

Ok this is exactly what I did:

Went to Places > Home Folder
Checked off "Show Hidden Files"

Went to .mozilla/firefox/_.default/
Here, I created a folder called "chrome"
Inside it, I made a blank .css file called "userContent.css"
I inserted the following line (as shown here in step 3: [http://ttcs.wordpress.com/2008/02/12/how-to-apply-word-wrap-to-text-files-viewed-in-mozilla-firefox/](http://ttcs.wordpress.com/2008/02/12/how-to-apply-word-wrap-to-text-files-viewed-in-mozilla-firefox/)) into the .css file:

pre { white-space: -moz-pre-wrap !important; }

Quit Firefox, opened it again. Then I tried to zoom-in on text to see if it would wrap it, but it didn't work. What did I do wrong? :(

---

### Post by jtarin on 2011-07-07
Open your Browser, 
type in the url bar "about:config:" 
proceed through the warning and 
in the search bar type "wrap" 
and double-click on "view_source.wrap_long_lines" to change to true 
and the exit and check. Might have to restart.

---

### Post by WubiAR on 2011-07-07
Ok I followed your instructions jtarin, but it still doesn't seem to  work. When I zoom in, I still have to click the slider over horizontally when viewing the text....

---

### Post by lovinglinux on 2011-07-07
> **WubiAR said:**
> Ok this is exactly what I did:

Went to Places > Home Folder
Checked off "Show Hidden Files"

Went to .mozilla/firefox/_.default/
Here, I created a folder called "chrome"
Inside it, I made a blank .css file called "userContent.css"
I inserted the following line (as shown here in step 3: [http://ttcs.wordpress.com/2008/02/12/how-to-apply-word-wrap-to-text-files-viewed-in-mozilla-firefox/](http://ttcs.wordpress.com/2008/02/12/how-to-apply-word-wrap-to-text-files-viewed-in-mozilla-firefox/)) into the .css file:

pre { white-space: -moz-pre-wrap !important; }

Quit Firefox, opened it again. Then I tried to zoom-in on text to see if it would wrap it, but it didn't work. What did I do wrong? :(

I did some tests with *userContent.css* on Firefox 3.5, 3.6, 4.0 and 5.0. It seems to be working. However, I haven't tried your particular rule. What you did is correct tho.

---

### Post by jtarin on 2011-07-07
How about I give you a config for removing your slider?:P

---

### Post by jtarin on 2011-07-07
[This]("http://userscripts.org/scripts/show/2641") and GreaseMonkey.

---

### Post by jhi on 2011-12-05
The code is slightly different for newer versions of Iceweasel/Firefox. It should be:
pre { white-space: pre-wrap !important; }
I struggled with this for a long time as I like to view text files through my browser. Found on another forum. Good luck.

---

