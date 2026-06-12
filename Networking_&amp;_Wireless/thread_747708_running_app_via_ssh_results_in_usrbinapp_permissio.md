---
title: "running app via ssh results in /usr/bin/app permission denied"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by jimmy the saint on 2008-04-06
I appologize for the double post, but after thinking about it, this area seems more appropriate than General Help.

I installed HandbrakeCLI on my headless Ubuntu Gutsy server.  When I attempt to run it via SSH, I get the error "-bash: /usr/bin/HandBrakeCLI: Permission denied"

Do I need to do something special to be able to run apps through SSH?  

Thanks for any help.

JTS

---

### Post by jimmy the saint on 2008-04-06
I have tried to change the file permissions on the bianary....didnt help.  This is very frustrating.  Does SSH not allow binary execution, or would this likely be an issue on the server itself?

---

### Post by jetsam on 2008-04-06
Don't know about your specific problem, but ssh allows running binaries.  You can make sure nothing is wrong with your ssh by trying a common one like pico or vim.  

I would guess it's probably a problem with the installation of the program on the server.  I couldn't find it in the repositories, so I'm guessing you installed it from the website.  They don't seem to focus much on linux.  Maybe try installing it locally to make sure it works?

---

