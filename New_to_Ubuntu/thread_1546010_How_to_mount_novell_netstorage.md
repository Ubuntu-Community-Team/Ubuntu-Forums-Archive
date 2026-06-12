---
title: "How to mount novell netstorage?"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by Yaldair on 2010-08-04
Hello everyone,

At my university they use novell netstorage to enable you to access your drive at home. Now, I can do this with firefox but the interface is not really that great, so I'd rather use nautilus if possible.

I tried connecting to a server, and there is one way possible for me to see the folders on my drive. However, when I try to open a folder it fails to do so. So pretty much I can see the two "folders" that are available to me, but opening them is out of the question.

The way I get this far is by connecting to a server with the http protocol, rather than the https (which the University tells me to use).

I tried using the https protocol, but then it doesn't work at all. And I can't connect. I looked around this evening but can't find anything that works. Is there some way to mount a novell netstorage drive? Or am I forced to use firefox for this ? :(

Thanks in advance,


edit:

So, what I exactly did to "partly connect" to the server is in nautilius: File-->Connect to Server-->select webdav-->insert the servername without the https:// or webdavs:// protocol in front of it.

You get prompted for username+pass. I fill them in and see two drives I can basically select that are available to me. they are shown as driveX@servername but when I try to doubleclick on them they are changed into some file and I get an error message.

If I try to use the secure webdav (which I am supposed to use) I get an error message;
Error: HTTP Error: Internal Server Error
Please select another viewer and try again

---

### Post by MetaDark on 2010-09-09
My school is also using NetStorage. I am actually thinking of getting our school to use Ubuntu instead of ugh... Windows...

But, this is one major issue that I am having trying to get Ubuntu into a usable state for my School.

So far I customized the Live CD, Added some programs, changed the theme to elementary ( a really awesome gnome theme ) etc...

The method that you tried didn't work at all with me, I got the error message

> Could not display "davs://THESTORAGEURL/".

Error: Not a WebDAV enabled share
Please select another viewer and try again.

But I am still trying.

I will post back if I get any results.

---

### Post by MetaDark on 2010-09-09
I got to the point were you are at, when you said the URL I thought you meant the main URL not the MAINURL/oneNet/NetStorage... folder.

I am going to try to research this a bit further.

By the way Secure WebDav did work for me but it still gave the same result as the unsecure WebDav.

---

### Post by MetaDark on 2010-09-10
At least I found out that it actually connects to the server. If you type in the wrong user/password it prompts you to try again.

I also tested it on my school computer on my Live iPod Touch, but it did not help at all.

I am going to make a guide on this if I actually figure out how to get it to run...

---

### Post by MetaDark on 2010-09-10
I think I found the cause of this error, copy the URL you are trying to access ( with the https or http ) and paste it into the address bar of another browser, or restart your current one.

What do you know! It displays a server error!

So I guess somehow you need to find a way to access the URL without directly accessing it.

---

### Post by MetaDark on 2010-09-10
I found a file called TextView.html, the TextView icon redirects you to this html file.

The contents are;

```
<HTML>
<body>
<script language="JavaScript" type="text/javascript">
	var d = new Date();
	d.setFullYear(d.getFullYear()+1)
	document.cookie = "TextMode=1; path=/"
	window.top.location.href = "/oneNet/NetStorage"
</script>
</body>
```

I know html somewhat but I am not sure why this would work and why entering the URL directly would not.

---

### Post by MetaDark on 2010-09-12
I think I may give up on WebDav, I found an application that works for what I am doing, the only bad thing about it is that you have to be connected to the schools network to use it.

It's called ncpfs, if you are wondering.

---

