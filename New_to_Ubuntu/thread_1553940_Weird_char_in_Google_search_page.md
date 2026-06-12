---
title: "Weird char in Google search page"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by michaelbr on 2010-08-15
Greetings:
I'm new to Linux/Ubuntu, just installed 10.04. I'm using Google search engines for different languages (US, Portuguese & Chinese), what I found is when I switched to foreign languages in Google search (either Portuguese or Canada), I got weird char in my search page.

Here' the picture of my English search: [http://www.glowfoto.com/static_image/15-200853L/7689/jpg/08/2010/img4/glowfoto]("http://www.glowfoto.com/static_image/15-200853L/7689/jpg/08/2010/img4/glowfoto")
and here's my Portuguese search: [http://www.glowfoto.com/viewimage.php?img=15-200630L&rand=2832&t=jpg&m=08&y=2010&srv=img4]("http://www.glowfoto.com/viewimage.php?img=15-200630L&rand=2832&t=jpg&m=08&y=2010&srv=img4")

This is brand new installation, and I thought it was the language pack that's missing, so I went to Administration/Language Support and added Portuguese and Chinese, but the page still showed the same weird char (I think the language support is used to switch to other languages for your Linux and not for webpages).

My installation is Ubuntu 10.04 and the Google BR is using Unicode( UTF-8 ). I'm pretty sure it must be some configuration I'm missing. Can someone please tell me what the problem is and how to fix it?

---

### Post by AnGeLiX on 2010-12-22
Hi,

I just found a solution to that problem.

You have to set the languages if Firefox

Edit > Options > Content > Languages [Choose] > Remove the 'chrome' entry and add English and your language.

---

### Post by michaelbr on 2010-12-22
> **AnGeLiX said:**
> Hi,

I just found a solution to that problem.

You have to set the languages if Firefox

Edit > Options > Content > Languages [Choose] > Remove the 'chrome' entry and add English and your language.

Thanks AnGeLiX for your reply, the problem is solved.

---

