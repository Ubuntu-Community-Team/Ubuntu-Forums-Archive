---
title: "Saving Web pages"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by TeeSquare on 2009-02-11
I have started using Ubuntu 8.04.1 very recently (first experience of Linux) but have not succeeded in saving web pages. I used File>SaveAs (Webpage, complete) and it went into my home folder as html, but when I tried to open it later offline, it seemed to be trying to access internet (progress bar creeping along) but the page content remained blank. Is there something I am missing?

This would happen sometimes with Windows98 which I have used so far, but generally a pop-up would provide a choice of connecting to internet or remaining off line. Choosing 'offline' (sometimes repeatedly) would in most cases allow the page to open. Does something of that sort happen in Linux?

I would like to read the pages only off-line to limit the time I remain connected (and vulnerable to viruses and increasing internet charges). Does Ubuntu have anything like the 'temporary internet files' which get saved automatically in Windows for viewing later?
Thanks, =TeeSquare=

---

### Post by Gannon8 on 2009-02-11
Look for a firefox addon. Downloading all the images will waste a lot of space.

When you go to File -> Save As, you don't download the images and other content. You store a text version of the page pretty much.

As for the temporary directory, it is /tmp. There are so few linux viruses so it shouldn't be a problem. As for internet prices, don't most ISPs sell you unlimited internet for a set price?

---

### Post by stanz on 2009-02-11
yeah - its the browser you want to save pages with. The firefox forum might also be worth checking out--for other advice on whats working well.
Saving webpages with your browser -- will do it as you expect it to be done!
Usually giving you 2 folders - html and ? {I forgot}.

I also believe there is a big difference between m$'s temp folder and any other.
It may not serve your purpose.

---

### Post by perlluver on 2009-02-11
You can use wget in a terminal, Applications>Accessories>Terminal then ```
wget http://www.google.com
```  I don't know if it stores photos, but it will download the web page.

---

### Post by hyperyoda on 2009-02-11
> **TeeSquare said:**
> I have started using Ubuntu 8.04.1 very recently (first experience of Linux) but have not succeeded in saving web pages. I used File>SaveAs (Webpage, complete) and it went into my home folder as html, but when I tried to open it later offline, it seemed to be trying to access internet (progress bar creeping along) but the page content remained blank. Is there something I am missing?

This would happen sometimes with Windows98 which I have used so far, but generally a pop-up would provide a choice of connecting to internet or remaining off line. Choosing 'offline' (sometimes repeatedly) would in most cases allow the page to open. Does something of that sort happen in Linux?

I would like to read the pages only off-line to limit the time I remain connected (and vulnerable to viruses and increasing internet charges). Does Ubuntu have anything like the 'temporary internet files' which get saved automatically in Windows for viewing later?
Thanks, =TeeSquare=

The command line program wget is great for saving webpages:
$ wget [http://whatever.org](http://whatever.org)

It can also download pages recursively and you can tell it what you want to exclude from the download.

In Firefox go to File->Save As (Ctrl-S) then click "Browse other folders" and down on the right hand corer you will see "Web Page, complete", click the arrows and select "Web Page, HTML only" then it will save the page in HTML in a single file.

Zach

---

### Post by jerrrys on 2009-02-11
zotero will save web pages with just a mouse click

[http://www.zotero.org/](http://www.zotero.org/)

---

### Post by TeeSquare on 2009-02-12
Thanks for all the inputs. I'll have to digest them slowly and try whatever I can understand over several days ! I'm REALLY an absolute beginner in Linux and computing generally (except for editing text in a word processor). All the command line stuff and dealing with applications is still a maze for me.
I'll report success or failure here in due course.
I don't really intend to do much downloading, and just wish to keep track of what I get through dial-up or a minimal broadband facility, as I may use either.
Thanks again, =TeeSquare=

---

### Post by mc4100 on 2009-02-12
> **TeeSquare said:**
> I would like to read the pages only off-line to limit the time I remain connected (and vulnerable to viruses and increasing internet charges).
Thanks, =TeeSquare=
You could use the "Print..." menu entry, the "print to file" dialog enables you to create a pdf which is ideal for on-the-go **reading**.

Edit: In fact maybe not, I'm not sure it'll handle images any better than save.

---

