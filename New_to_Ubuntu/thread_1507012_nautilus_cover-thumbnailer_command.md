---
title: "nautilus cover-thumbnailer command"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by a.sarkar on 2010-06-11
Hi,
I have already searched the internet, but couldn't find a suitable answer to this problem.
What is the command to set folder attribute such that it uses my custom  .folder.png as the folder icon in nautilus (lucid).

I know there is a script cover-thumbnailer (here's the [link]("http://software.flogisoft.com/cover-thumbnailer/en/")) which does the very same job that I am looking for, except that it uses its own cover thumbnails. I already have a script to prepare my own custom thumbnail, but I don't know how to set it, so that nautilus uses it as folder icon.

I tried the command 

```

gvfs-set-attribute . metadata::custom-icon .folder.png

```where the "dot" after gvfs-set-attribute denotes the current directory and .folder.png is my custom icon. However, the icons are two small. (Check screenshot-01.png)

If I use the cover-thumbnailer then somehow the folder icons are much larger (which I like). Check screenshot-02.png.

So my questions are 

i) what is the crux of the command that cover-thumbnailer uses that sets the icons larger, whereas my command does not do it.

ii) how do I revert back to the original folder icon via cli?

---

### Post by FLOZz on 2010-07-16
Cover thumbnailer uses the GNOME thumbnail factory.

You can find all the documentation about the GNOME thumbnail factory here :
[http://library.gnome.org/devel/integration-guide/stable/thumbnailer.html.en](http://library.gnome.org/devel/integration-guide/stable/thumbnailer.html.en)

And you can read the freedesktop thumbnail spec here :
[http://jens.triq.net/thumbnail-spec/](http://jens.triq.net/thumbnail-spec/)

Regards,

---

### Post by a.sarkar on 2010-07-17
Thanks FLOZz,
I will check the links.
Regards,

---

