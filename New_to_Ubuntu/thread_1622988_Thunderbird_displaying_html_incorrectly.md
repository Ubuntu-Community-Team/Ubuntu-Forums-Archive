---
title: "Thunderbird displaying html incorrectly?"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by Falc7 on 2010-11-16
Ok, at work, they are trying to get a new signature implimented, but having some problems:

Person A send us the signature, its not in code format, I think no problem, so i edit the signature (not in code form) in 'new message' in thunderbird, select all, then click insert html and copy that into the signature settings. But when i test it by clicking on create new email, it looks all wierd, the style, font size and format are all different. Even though it all looked fine in the new message.


So person A then sends me the notepad file with the signature in code format, I notice that it looks completely different from the code thunderbird generated. Anyway i edit this htlm code directly, the signature all looks fine using this website: [http://htmledit.squarefree.com/](http://htmledit.squarefree.com/)
I then copy this code into the thunderbird signature part, I click new message, everything looks fine, the formatting is correct. I send the email as a test, and when it reaches a different email box being viewed in TB on the same computer, it all looks different, the formatting is wrong. Whats going wrong?

If you want to test, here is the code:

  ```
<style>
#sig a:link{color: #690;}
#sig a:visited{color: #690;}
#sig a:hover{color: #690;}
</style>
<div id="sig" style="-webkit-text-size-adjust:none;line-height: 2px; margin: 6px 0; padding: 4px; border-top: 1px #999 dotted; border-bottom: 1px #999 dotted; font-family: 'Lucida Grande', Verdana, Arial, Sans-Serif; font-size: 10px; color: #555;" >

  <p><strong style="color: #333333;">Name</strong> Title, Location</p>
  <p><strong style="color: #336699;">Organisation</strong> <strong style ="color: #8B0000;"> Location</strong> <strong style="color: #333333;"> | City</strong>
  <p>tel: <a style="color: #336699; text-decoration: none;">phone number</a> web: <a href="http://www.website.org" style="color: #336699; text-decoration: none; border-bottom: 1px #999999 dotted;">website.org</a> email: <a href="mailto:email@email.org" style="color: #336699; text-decoration: none; border-bottom: 1px #999 dotted;">email@email.org</a></p>
</div>
```

Screenshots 
The way it should be, and the way it looks when i click create new email:
[IMG]http://oi56.tinypic.com/1zzhuee.jpg[/IMG]

The way it is received on the same computer from which it was sent:
[IMG]http://oi51.tinypic.com/1zb5s78.jpg[/IMG]

All using Thunderbird

---

### Post by Falc7 on 2010-11-18
bump

---

