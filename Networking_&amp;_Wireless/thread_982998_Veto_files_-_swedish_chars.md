---
title: "Veto files - swedish chars"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by sittingducks on 2008-11-15
How can i setup Samba to NOT view files with åäö in them?

Tried ->

veto files = /*å*/*ä*/*ö*/

and

veto files = /*\xe5*/*\xe4*/*\xf6*/

Neither seem to work.

/Thanks

---

### Post by puppywhacker on 2008-11-15
[techrepublic link]("http://articles.techrepublic.com.com/5100-10878_11-1053301.html")

"Note that placing the veto directive in the [Homes] section does not prevent the files in the restricted list from appearing in other shares"

I think your question is very specific, I'm specially puzzeled by why you want to do this, but I guess you can do it after a lot of debugging :(

goodluck

---

### Post by sittingducks on 2008-11-15
> **puppywhacker said:**
> 
I think your question is very specific, I'm specially puzzeled by why you want to do this, but I guess you can do it after a lot of debugging :(

goodluck

Solved it by using UTF-7 :lolflag:

---

