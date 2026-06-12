---
title: "Portable Ubuntu - how do I start it?"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by Sholto on 2010-06-15
I previously posted about how I could simultaneously view my Windows and Linux files/windows on the same machine, and was pointed towards [Portable Ubuntu]("http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows").  It seemed just what I wanted, but the link to the download page is dud, as is the link to the company (demonccc).
I found the zip file elsewhere and duly downloaded and unzipped it.  However the page above instructs us start it with the batch file [FONT=Courier New]run_portable_ubuntu[/FONT].  No such file exists.
The 2-line ReadMe.txt tells us to start it with pubuntu_Xming.exe.  However this just bombs out with the error message "No valid configuration file".  It gives us no hint as to what that file should be.
Has anyone cracked this yet?

---

### Post by ankspo71 on 2010-06-15
Hi,
I haven't tried portable ubuntu before, and I don't have windows installed, but this topic caught my interest.

Have you downloaded it from here? 
[http://sourceforge.net/projects/portableubuntu/files/](http://sourceforge.net/projects/portableubuntu/files/)

I see there are versions UNO DOS and TRES (they can be seen if you scroll down a bit). In the TRES folder there is a 587mb exe file called Portable_Ubuntu_TRES.exe. That looks like the file I would have downloaded if I wanted to try it. 

When I first looked for portable ubuntu a moment ago, it wanted me to download a 7zip file named Xming_for_Portable_Ubuntu_DOS.7z (much smaller) from the same site I just mentioned above. When you said you had to extract your download, I was thinking you might have downloaded that one instead. 

Hope this helps, and Good luck.

---

### Post by Sholto on 2010-06-16
Many thanks ankspo. Yes I did download Xming_for_Portable_Ubuntu_DOS.7z, and maybe this is where I went wrong. I will try numero tres now.
Watch this space...!

---

### Post by Sholto on 2010-06-16
Well I tried running the pubuntu executable, as recommended [here]("http://www.kabatology.com/04/03/portable-ubuntu-9-10-for-windows-runs-ubuntu-inside-windows/").  However it was instantly pounced upon by Norton, with the message:
* colinux.daemon.exe (Suspicious.Emit).  This Heuristic Virus has been removed.*
The splash screen is left hanging.
Is this just Norton being too anal, or is there a problem with colinux?
I think it comes from an Argentinian site - anyone know anything about these guys?

---

### Post by ankspo71 on 2010-06-16
Hi,
I'm thinking that it's just a heuristic false positive because colinux has been around for a while and I know it has been mentioned here often. I searched for your norton virus warning and I didn't see anything either. It appears to me that PortableLinux might use colinux as the core linux system, just like andlinux does.

You might be interested in looking at these links to see what colinux is, or to check on alternatives to PortableLinux.
[http://www.andlinux.org/](http://www.andlinux.org/)
[http://www.colinux.org/](http://www.colinux.org/)

Hope that helps.

---

