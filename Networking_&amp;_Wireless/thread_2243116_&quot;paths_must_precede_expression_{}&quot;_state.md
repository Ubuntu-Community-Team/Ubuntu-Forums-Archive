---
title: "&quot;paths must precede expression: {}&quot; statement"
date: 2014-09-06
forum: Networking &amp; Wireless
---

### Post by Herbon on 2014-09-06
I'm working on a Bash script to move old folders from one NAS to another after ping replies.

The error I'm getting is "paths must precede expression: {}" after the following line...

```

#Path to XX.XX  NAS drive, and folder move not file. Moves folder older than 45 days
find ./ -mtime +130 -type d -exec mv -t {}  /run/user/1000/gvfs/smb-share:server=XX.XX.XX.XX,share=video/"_Archived Movies"/ \; {} +


```

Not sure what the problem is.

PS how do I test run this or try it with actually moving folders?

Thanks

---

### Post by steeldriver on 2014-09-06
What are you trying to do exactly? it looks like you have too many {} , in particular the one after the -t is probably misplaced (the **-t dir** is where you want to move stuff** to** - aka the **t**arget)

If you are truing to move the dirs found under your current directory to the /run/user/1000/gvfs/smb-share:server=XX.XX.XX.XX,share=video/"_Archived Movies"/ directory you probably want something like

```

find ./ -mtime +130 -type d -exec **mv -t /run/user/1000/gvfs/smb-share:server=XX.XX.XX.XX,share=video/"_Archived Movies"/ {} +**

```

(although the ./ is superfluous I think since find will start from the current dir by default)

You can do a dry run by adding an echo i.e.

```

find ./ -mtime +130 -type d -exec **echo **mv -t /run/user/1000/gvfs/smb-share:server=XX.XX.XX.XX,share=video/"_Archived Movies"/ {} +

```

---

### Post by Herbon on 2014-09-06
A new error challenge after running the following

```

find ./ -mtime +130 -type d -exec **mv -t /run/user/1000/gvfs/smb-share:server=XX.XX.XX.XX,share=video/"_Archived Movies"/ {} +**
```

Error 

```

mv: cannot move &#8216;./The.Collection (1998)&#8217; to &#8216;/run/user/1000/gvfs/smb-share:server=10.10.2.5,share=video/_Archived Movies/The.Collection (1998)&#8217;: Input/output error


```

The new location is ping-able and when I c/p the command in the term. it was works, but the script gives me an error.

---

