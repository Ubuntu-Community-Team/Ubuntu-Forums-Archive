---
title: "Firefox 3.6, java and zotero"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Karen Forrest on 2010-01-26
I wonder if anyone can help me get zotero working with firefox 3.6 - I've been through the zotero forums and these ones too and followed the instructions as far as I understand them. 
I have installed the java6-plugin and I've made a symbolic link to  the plugins folder as suggested here  [http://ubuntuforums.org/showthread.php?t=1387443&highlight=java6+plugin](http://ubuntuforums.org/showthread.php?t=1387443&highlight=java6+plugin)
Then I've followed the instructions at the zotero forums here
[http://forums.zotero.org/discussion/10439/firefox-36/#Item_16](http://forums.zotero.org/discussion/10439/firefox-36/#Item_16)
When I try to load the open office integration extension I get a message telling me java isn't working, so I think FF is still not recognising the plugin.
Now I'm stuck and I think I've gone well beyond my level of understanding - and I still have unreferenced papers which are due to be handed in...
Alternatively, advice on reverting to FF3.5 to solve the problem would be fine - I upgraded by opening FF as root and using help>check updates. 
Thanks,
Karen

---

### Post by tantemahuta on 2010-01-28
Hi there,

I had the same problem with unreferenced papers here. 
This: [http://ubuntuforums.org/showthread.php?t=1305603](http://ubuntuforums.org/showthread.php?t=1305603) and then this: [http://ubuntuforums.org/showthread.php?p=8734825](http://ubuntuforums.org/showthread.php?p=8734825) helped me - I hope it will resolve your problem too.

cheers
Michael

---

### Post by Karen Forrest on 2010-02-01
Thanks for trying - but that still hasn't helped. Despite following all the instructions and then the links through to [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) and doing everything there, FF is still not recognising Java. And so Zotero isn't working. 
I really would rather go back to FF3.5 if that's what's needed to get it going again, but I'm not sure how?
Karen

---

### Post by neanderslob on 2010-12-04
Alright check it out, if anyone's still having problems.  I enabled the Canonical Partner repository in synaptic, and ran sudo apt-get install sun-java6-plugin.  THEN, and here was the critical part, I had to go back and get rid of the old icedtea java stuff so I ran "sudo apt-get remove icedtea*" Restarted both programs and it's working like a charm now.  I don't know if this is still bugging the original poster but maybe this'll help someone.  Zotero really is a fantastic program, especially for someone like me who HATES bibliographies.  Cheers!

:guitar:

---

