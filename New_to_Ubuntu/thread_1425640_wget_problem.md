---
title: "wget problem"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by mvalviar on 2010-03-09
I suddenly started getting this when I invoke wget ```
mvalviar@mumee:~$ wget www.example.com
Error parsing proxy URL wpad://: Unsupported scheme.

```

What gives? I did a google search for this but the discussion is all greek to me.

---

### Post by ubudog on 2010-03-09
If wget doesn't work, you can go to the site in firefox and right click and select "Save Page As"  That will work.

---

### Post by dannyboy79 on 2010-03-09
> **mvalviar said:**
> I suddenly started getting this when I invoke wget ```
mvalviar@mumee:~$ wget www.example.com
Error parsing proxy URL wpad://: Unsupported scheme.

```

What gives? I did a google search for this but the discussion is all greek to me.

i didn't think wget downloaded entire webpages! i thought wget was for downloading files from the internet. i could be wrong but then i'll be learning something new.

---

### Post by J V on 2010-03-09
The webpage is just a file with links to other files, it should just download it but it won't look right when opened... It looks like you are using a proxy or something? idk :?

---

### Post by mvalviar on 2010-03-09
I need wget to spider a website to check for brokenlinks. 

I'm getting a similar error message with python's urllib. ```
IOError: [Errno url error] invalid proxy for http: 'wpad://'
```

I don't believe I'm using a proxy. I don't even know how to set it. How do I check for it?

---

### Post by mvalviar on 2010-03-09
Ok. I saw it at System>Preferences>Network Proxy

It is set to direct connection

---

### Post by gmargo on 2010-03-09
What is the site?  Obviously not example.com.

---

### Post by Anthony Fok on 2010-03-11
> **mvalviar said:**
> I suddenly started getting this when I invoke wget ```
mvalviar@mumee:~$ wget www.example.com
Error parsing proxy URL wpad://: Unsupported scheme.

```

What gives? I did a google search for this but the discussion is all greek to me.

Something in GNOME (perhaps?) has set the environment variable

[INDENT]http_proxy=wpad://[/INDENT]

which Wget (as of version 1.12) does not support.  For now, you may use the following workaround:

```
$ unset http_proxy
$ wget http://www.example.com/
```

or consider using e.g. lftpget or other handy download commands.

Hope this helps!

Anthony

---

