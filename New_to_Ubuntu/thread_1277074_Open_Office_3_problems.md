---
title: "Open Office 3 problems"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by bsmith52 on 2009-09-27
I managed to replace the Open Office that came with my ubuntu 8.10 with Open Office 3 (I needed a feature it had).  Now I want to use that software to open MS Word docs that people send me. So 3 things:
1, How do I make my Open Office 3 one of the applications that I can choose to open a downloaded file (it is in Applications -> Office -> Open Office Writer 3.10, but not a choice when I open a downloaded doc).
2. Where are the downloaded docs (I could open Open Office and open the downloaded file if I knew where it was!).
3. If I wanted to launch the Open Office program from a terminal session, what command could I use (or does Open Office require a GUI environment to work in)?
Thanks,
Bill

---

### Post by wilee-nilee on 2009-09-27
> **bsmith52 said:**
> I managed to replace the Open Office that came with my ubuntu 8.10 with Open Office 3 (I needed a feature it had).  Now I want to use that software to open MS Word docs that people send me. So 3 things:
1, How do I make my Open Office 3 one of the applications that I can choose to open a downloaded file (it is in Applications -> Office -> Open Office Writer 3.10, but not a choice when I open a downloaded doc).
2. Where are the downloaded docs (I could open Open Office and open the downloaded file if I knew where it was!).
3. If I wanted to launch the Open Office program from a terminal session, what command could I use (or does Open Office require a GUI environment to work in)?
Thanks,
Bill

1= right click on document choose open with
2= Home if you haven't chosen another place, personally I have stuff download to my desktop, the download asks you where you want them.
3= I don't know this one, but since open office has multiple programs it seems easier to just open it like normal, and you can adjust it to work faster there is info on the web to tweak OO and you can set it to quick start as well.

I hope this is helpful.

---

### Post by Amstell on 2009-09-27
3.  Use this command to open Ooo Writer.  Just replace writer with whatever you need opened.

```
ooffice -writer
```

---

### Post by Amstell on 2009-09-27
3.  Use this command to open Ooo Writer.  Just replace writer with whatever you need opened.

```
ooffice -writer
```

---

### Post by bsmith52 on 2009-09-28
> **bsmith52 said:**
> I managed to replace the Open Office that came with my ubuntu 8.10 with Open Office 3 (I needed a feature it had).  Now I want to use that software to open MS Word docs that people send me. So 3 things:
1, How do I make my Open Office 3 one of the applications that I can choose to open a downloaded file (it is in Applications -> Office -> Open Office Writer 3.10, but not a choice when I open a downloaded doc).
2. Where are the downloaded docs (I could open Open Office and open the downloaded file if I knew where it was!).
3. If I wanted to launch the Open Office program from a terminal session, what command could I use (or does Open Office require a GUI environment to work in)?
Thanks,
Bill

Thanks for your response.

I guess that I wasn't clear as to the problem that I had. This is what I said:

*1, How do I make my Open Office 3 one of the applications that I can choose to open a downloaded file (it is in Applications -> Office -> Open Office Writer 3.10, but not a choice when I open a downloaded doc).*

What I ment to say was: When I click on a file to open, there are options as to programs to use, but Opeen Office is not one of the choices.  It will also give me an option to locate the application by showing me locations on my hard drive.  But since I don't know where Open Office is on my hard drive, I can't use that option.

My second question is resolved. I right click on the file, and use the "Open containing foller" option to let me know where the file is located.

The third response is helpful, but not complete for me.  When I tried your terminal command, I got "Command not found". I must need to know where the oofice progam is located, so that I can do something to it so that my command prompt can find it and execute it from my default location (my desktop).

Thanks again for your response!

Bill

---

### Post by rockstarrem on 2009-09-28
Binaries are usually located in /usr/local/bin or /usr/bin .

---

### Post by jmszr on 2009-09-28
bsmith52,

For #1) Try: Open Writer, Go to Tools > Options > Load/Save > Microsoft Office > Make sure the boxes are check marked. That's a possibility.

---

### Post by pgibson on 2009-09-28
Forgive my presumption, but regarding your second question, I may have an additional solution.  If by "download" you are referring to using a web browser, I've set firefox to download things to my desktop so that I can easily see them and won't forget them and can put them where I like.

Would this be useful?  In firefox this can be done from **Edit -> Preferences -> Main** where one can set firefox's default download location.

Hope that helps give you options.

---

### Post by sandyd on 2009-09-28
> **bsmith52 said:**
> Thanks for your response.

I guess that I wasn't clear as to the problem that I had. This is what I said:

*1, How do I make my Open Office 3 one of the applications that I can choose to open a downloaded file (it is in Applications -> Office -> Open Office Writer 3.10, but not a choice when I open a downloaded doc).*

What I ment to say was: When I click on a file to open, there are options as to programs to use, but Opeen Office is not one of the choices.  It will also give me an option to locate the application by showing me locations on my hard drive.  But since I don't know where Open Office is on my hard drive, I can't use that option.

My second question is resolved. I right click on the file, and use the "Open containing foller" option to let me know where the file is located.

The third response is helpful, but not complete for me.  When I tried your terminal command, I got "Command not found". I must need to know where the oofice progam is located, so that I can do something to it so that my command prompt can find it and execute it from my default location (my desktop).

Thanks again for your response!

Bill


OpenOffice Writer: /usr/bin/openoffice.org3 -writer %U
OpenOffice Calc: /usr/bin/openoffice.org3 -calc %U
OpenOffice Base: /usr/bin/openoffice.org3 -base %U
OpenOffice Draw: /usr/bin/openoffice.org3 -draw %U
OpenOffice Impress: /usr/bin/openoffice.org3 -impress %U
OpenOffice Math: /usr/bin/openoffice.org3 -math %U

---

### Post by Hagar Delest on 2009-09-28
Or just type **soffice** to launch the start center.

---

