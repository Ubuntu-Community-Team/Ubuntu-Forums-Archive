---
title: "Probelem with Wine fonts"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by kestrel1 on 2009-03-06
I have just installed Wine & when I go to the wine config I get this screen
[ATTACH]105499[/ATTACH]
Any ideas.

---

### Post by kestrel1 on 2009-03-06
Anyone?

---

### Post by albandy on 2009-03-06
First disable desktop effects to test if works ok, if not
try installing msttcorefonts

---

### Post by kestrel1 on 2009-03-06
Sorry should have mentioned that I have already disabled Desktop Effects, changed the font type in Appearance etc. No real difference apart from the fonts are totally unreadable
[ATTACH]105501[/ATTACH]
I have had problems with the msttcorefonts install, see this thread for info:
[http://ubuntuforums.org/showthread.php?t=1087655](http://ubuntuforums.org/showthread.php?t=1087655)
I have move the arial & times fonts from the msttcorefonts folder to the /.wine/drive_c/windows/Fonts folder
No difference.
It could be that the msttcorefonts are not recognized correctly. I will look into manually installing these fonts if there is a way.

---

### Post by kestrel1 on 2009-03-06
From what I can see I should be able to install the msttcorefonts manually, but I need access to the sourceforge website, which isn't possible here. I will have to download them over the weekend & try to get them installed on Monday. This getting rather annoying not having access to soureforge. I may have to nag the ISP to allow access, but I have a feeling they will not do it.

---

### Post by Mze on 2009-03-06
Find solution [here]("http://ubuntuforums.org/showthread.php?t=1026538&page=2")

---

### Post by kestrel1 on 2009-03-06
> **Mze said:**
> Find solution [here]("http://ubuntuforums.org/showthread.php?t=1026538&page=2")
Thanks for the link, but this hasn't worked either. I do not have a problem with Open Office as suggested in the link, but I know exactly what that problem was like, because I used to suffer from that, but got around another way, which I cannot think of right now.
I am reasonably sure that this is down to the inability to install the msttcorefonts issue in my other thread posted above.
I will try & get the fonts downloaded over the weekend & give it another try. If not I might just drop the machine back to 8.04.

---

### Post by 4Orbs on 2009-03-06
The solution, [try this.]("http://ubuntuforums.org/showthread.php?p=6667437#post6667437")

---

### Post by kestrel1 on 2009-03-09
4Orbs, thans very much. That seems to have sorted it out. I was able to get the msttcorefonts installed this morning, using the normal method. 
I had to contact the ISP's filtering people, because I was unable to download clamwin, which I use on the Windows machines here. They unblocked this on Friday & said it would be ready the following day. As I am not here on a Saturday I couldn't test that. Anyway, came in this morning & thought I would try installing the msttcorefonts with apt-get & it worked, so obviously how they had blocked clamwin was also affecting the download of the corefonts. 
This didn't sort thew problem, but 4Orbs link worked like a charm. Once again thanks 4Orbs.

---

