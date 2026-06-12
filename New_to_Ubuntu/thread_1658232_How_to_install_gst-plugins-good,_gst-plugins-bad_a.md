---
title: "How to install gst-plugins-good, gst-plugins-bad and gst-plugins-base?"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by Emack on 2011-01-02
Hi to everyone, 
this is my first post in this forum! I'm a newbie ubuntu user from Italy, and I'd like to enhance my knowledge about this distribution day by day :)

Actually, I'm unable to find gst-plugins-good, gst-plugins-bad and gst-plugins-base plugins packages for GStreamer in my Software Center. When I download the sources and try to configure them, I get the following error message: 

```
configure: No package 'gstreamer-0.10' found
configure: error: no gstreamer-0.10 >= 0.10.31 (GStreamer) found

```

Can anyone help me? Thanks in advance.

---

### Post by Miter_J on 2011-01-02
Hi, welcome to the world of Linux~ I'm sure you'll enjoy it~
I am not very familiar too, but hope this would help.
That first sentence shows that you don't have the package 'gstreamer-0.10'
So, use this
```
sudo apt-get install gstreamer-0.10
```
and then try it again.
Good luck~

---

### Post by Miter_J on 2011-01-02
Hey, Emack. I wonder whether that worked~
If that worked, remember to mark this thread as [SOLVED].
Enjoy yourself~

---

### Post by no2498 on 2011-01-02
type gstreamer in your package manager click search

you need goog,bad,ugly, and 10

---

### Post by Emack on 2011-01-02
> **Miter_J said:**
> Hi, welcome to the world of Linux~ I'm sure you'll enjoy it~
I am not very familiar too, but hope this would help.
That first sentence shows that you don't have the package 'gstreamer-0.10'
So, use this
```
sudo apt-get install gstreamer-0.10
```and then try it again.
Good luck~
Unable to find the package. :(

---

### Post by Emack on 2011-01-02
> **no2498 said:**
> type gstreamer in your package manager click search

you need goog,bad,ugly, and 10

I only find packages with similar names, but not the same.

---

### Post by puntigamer on 2011-01-02
Hey buddy,

just type "gst" in the Synaptics, scroll down, and you will be able to find your necessary stuff ;)

It has to work! :)
Best wishes with Ubuntu!!

---

### Post by Elfy on 2011-01-02
What are you finding then?

0.10.31 (GStreamer) found implies you're running natty narwhal?

What does 

```
apt-cache search -n gstreamer0.10-plugins
``` run from a terminal tell you

---

### Post by Emack on 2011-01-02
```
emanuele@emanuele-laptop:~$ apt-cache search -n gstreamer0.10-plugins
gstreamer0.10-plugins-base - Plug-in GStreamer dall'insieme "base"
gstreamer0.10-plugins-base-apps - Programmi di aiuto Gstreamer dall'insieme "base"
gstreamer0.10-plugins-base-dbg - Plug-in GStreamer dall'insieme "base"
gstreamer0.10-plugins-base-doc - Documentazione per i plug-in GStreamer dall'insieme "base"
gstreamer0.10-plugins-bad - Plugin GStreamer dal gruppo "bad"
gstreamer0.10-plugins-bad-dbg - GStreamer plugins from the "bad" set (debug symbols)
gstreamer0.10-plugins-bad-doc - Documentazione GStreamer per i plugin dal gruppo "bad"
gstreamer0.10-plugins-ugly - Plugin Gstreamer per il gruppo "ugly"
gstreamer0.10-plugins-ugly-dbg - GStreamer plugins from the "ugly" set (debug symbols)
gstreamer0.10-plugins-ugly-doc - Documentazione GStreamer per i plugin dal gruppo "ugly"
gstreamer0.10-plugins-bad-multiverse - GStreamer plugins from the "bad" set (Multiverse Variant)
gstreamer0.10-plugins-bad-multiverse-dbg - GStreamer plugins from the "bad" set (Multiverse Variant)
gstreamer0.10-plugins-good - GStreamer plugins from the "good" set
gstreamer0.10-plugins-good-dbg - GStreamer plugins from the "good" set
gstreamer0.10-plugins-good-doc - GStreamer documentation for plugins from the "good" set
gstreamer0.10-plugins-ugly-multiverse - GStreamer plugins from the "ugly" set (Multiverse Variant)
gstreamer0.10-plugins-ugly-multiverse-dbg - GStreamer plugins from the "ugly" set (Multiverse Variant)

```So, gstreamer0.10-plugins-bad and gst-plugins-bad are the same? If yes, I already installed these plugins :lol:

---

### Post by ap2011 on 2011-04-12
I have installed all the plugins ,but I am getting the problem :    GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed   GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed     Please reply anyone.

---

