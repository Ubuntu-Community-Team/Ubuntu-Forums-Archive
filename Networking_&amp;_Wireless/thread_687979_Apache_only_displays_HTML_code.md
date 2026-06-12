---
title: "Apache only displays HTML code"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by fattom23 on 2008-02-04
I'm new to web design, but I managed to install the Apache server version 2.  It worked for a little while, but now it only seems to be showing html code rather than the properly rendered page.  When I open the file from the local disk in my browser, it displays properly.  However, when I pull it up over the internet, all I get in my window is the raw code.  For example, go here:

[www.fatmanwebdesign.com/display.html](www.fatmanwebdesign.com/display.html)

That code renders just fine when I pull it from the local disk.  If it helps any, IE renders it partially, but not completely.  Any ideas (or advice on what to post to enable someone to actually help me)?  Any help would be greatly appreciated.

---

### Post by fattom23 on 2008-02-04
Quick Correction, as I just tested it again.  IE actually displays the page perfectly.  No other browser does, however.  Thanks again.

---

### Post by dmizer on 2008-02-04
because "display" is not a recognized html file name according to apache.  if you rename "display.html" as "index.html" or if you define "display.html" and being a valid html file name, it will render as a web page in firefox and opera.

that IE displays the page is simply that it's programed to open any .html file as a web page.

also, if you have php installed, you could just give the file a .php extension and it should render correctly, like so: [edit]removed link, as it's no longer needed[edit]

---

### Post by fattom23 on 2008-02-05
adding the php file extension did something.  It caused my frames to at least display, albeit with the raw code for each frame displayed in it.  How do I define .html to be a web site in apache?  Thanks a lot for the help, btw.

Check out
[www.fatmanwebdesign.com](www.fatmanwebdesign.com)
To see what I mean.

---

### Post by fattom23 on 2008-02-05
I cleared my browser cache completely rather than using the reload button, and, miraculously, it works!  Just out of curiosity, though, why couldn't Apache recognize display.html as a webpage?  Is it a special reserved file name that I didn't know about?  Thanks.

---

### Post by dmizer on 2008-02-05
no ... apache only displays special reserved names as webpages, like "main.html" "index.html", and a handful of others which i cannot recall at the moment.  in order to get it to show "display.html" as a webpage, you would have to add it to a config file, but changing it to .php is (in my opinion) preferable.

i am not a professional though, so you should research this on your own and draw your own conclusions.

---

### Post by patryk77 on 2008-02-05
[http://www.developershome.com/wap/wapServerSetup/tutorial.asp?page=settingUpMIME](http://www.developershome.com/wap/wapServerSetup/tutorial.asp?page=settingUpMIME)

More likely your MIME types aren't properly defined.

Apache doesn't display any content, it just tells the browser "This is a file of type ... (HTML, or MP3, or MIDI, etc.)"

So you need to specify that a .htm or .html extension is an HTML file

---

