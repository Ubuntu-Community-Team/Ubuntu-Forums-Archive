---
title: "Help Ubuntu Page not rendering correctly"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by boojeboy on 2009-02-27
Who maintains: 

[https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)

I want to help out and noticed the pages only render correctly in Internet Explorer and neither FireFox nor Google Chrome.

Where do I file a bug about this page?

Thanks!

---

### Post by ikisham on 2009-02-27
Here it renders perfectly in FF 3.0.6 (Hardy). Try to wipe the cache or just wait, for it may be some other problem.

---

### Post by MarblePanther on 2009-02-27
Renders fine here, albeit a little too narrow (unless that's what you mean)

[ATTACH]104820[/ATTACH]

Oh, btw, Firefox 3.0.6 on Intrepid

---

### Post by boojeboy on 2009-02-27
I've tried on FireFox 3.0.6 and Google Chrome....
It looks totally fine in Internet Explorer. I even copied the files down in a WYSIWYG HTML tool and it rendered fine in the preview but jumbled in Firefox. 
Of course, the wiki is not in HTML, so there's only so much I can do to edit it. I did a rough diff of the wiki-HTML and saw no meaningful differences between some that look good and those that didn't.

This one [https://help.ubuntu.com/community/InstallLirc/Feisty]("https://help.ubuntu.com/community/InstallLirc/Feisty") renders just fine. 

thanks!

---

### Post by Ms_Angel_D on 2009-02-27
Funny I get the same result as the OP on that page and I'm running FF 3.0.6 in Intrepid. But when I login it looks fine, very strange. I'm not sure who maintains it though.

---

### Post by boojeboy on 2009-02-28
> **MetalHellsAngel said:**
> Funny I get the same result as the OP on that page and I'm running FF 3.0.6 in Intrepid. But when I login it looks fine, very strange. I'm not sure who maintains it though.

Same on WINXP btw, gotta be some kinda bug in the wiki-html, maybe cookie related. weird.

---

### Post by MarblePanther on 2009-02-28
Huh, I take it back.  I didn't scroll down to that particular area.  It is also the same here.

[ATTACH]104870[/ATTACH]

---

### Post by Old_Grey_Wolf on 2009-02-28
The image appears to be defined twice in the HTML

> <link rel="Appendix" title="install_dialog.png" href="/community/InstallLirc/Hardy?action=AttachFile&amp;do=view&amp;target=install_dialog.png">
<link rel="Appendix" title="install_dialog.png size=200 x 200" href="/community/InstallLirc/Hardy?action=AttachFile&amp;do=view&amp;target=install_dialog.png+size%3D200+x+200">


Also the / at the end of this line just before the </td> tag appears to be an error. The extra / may malform the table.

> <td colspan="1" rowspan="1" style="text-align: center"><p class="line862"> <img alt="install_dialog.png" class="attachment" src="/community/InstallLirc/Hardy?action=AttachFile&amp;do=get&amp;target=install_dialog.png" title="install_dialog.png" **[COLOR="DarkRed"]/[/COLOR]**> </td>


---

### Post by thtrgremlin on 2009-02-28
Well, it is a community wiki, so while I am sure there are administrators, anyone with a launchpad account can log in and fix it. Unfortunately, I am not that awesome at html, but I will look at it and see if anything else really stands out.

---

### Post by MarblePanther on 2009-02-28
Here it is with X-ray:

[ATTACH]104871[/ATTACH]

---

### Post by thtrgremlin on 2009-02-28
It is a wiki, and taking a look at some other pages, I think this wiki was generated and ran into some unanticipated problems, or the writer was only testing with IE (huh?).

Anyway, I feel I fixed the page in a reasonable way. Let me know what you think.

I am curious what it looked like in IE, but how many people use IE on Ubuntu?

---

### Post by MarblePanther on 2009-02-28
Very nice.  Looks good to me now. (firefox 3.0.6)

---

### Post by Ms_Angel_D on 2009-02-28
Yes it renders nicely now :)

---

### Post by boojeboy on 2009-03-02
Cool thanks!

---

