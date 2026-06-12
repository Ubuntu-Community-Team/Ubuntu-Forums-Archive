---
title: "School LAN administration"
date: 2014-04-11
forum: Networking &amp; Wireless
---

### Post by wiliam2 on 2014-04-11
Hello!

I'm working as volunteer at a primary school where exist close to 23 machines (used by teachers, students and employees).

Do you guys know if there is some open source project to control all these machines (Ubuntu 12.04 LTS) as if it were one?

I mean we need to update all these machines at once and periodically install new software.

Note1: all machines are connected in LAN and we have full access.
Note2: some tutorial or guide would be awesome.

Thanks!

---

### Post by Lars Noodén on 2014-04-11
I would look at Ansible or Puppet these days.  It might be useful to enable Wake-On-LAN so that you can have the server or gateway machine turn everything on for updating.  That way they can be kept turned off when not in use.

---

### Post by SeijiSensei on 2014-04-11
Another option is the [Linux Terminal Server Project]("http://ltsp.org/").  This requires a central server on which all the sessions run.  The client PCs are basically just used as display terminals.  This type of setup is much easier to manage centrally since there is only one image that all the users share.  Performance depends on the power of the server, of course.  An elementary school might not want to invest in the added hardware.

---

### Post by risk3715 on 2014-04-11
I have a mobile lab of 30 linux machines currently in use at one of the schools I manage. I've found that my best option to manage them currently is to use clusterssh or similar programs. I prefer to do everything in terminal anyway, especially for administration. I also setup Epoptes on them, but so far it doesn't get used much.

I haven't checked the rules yet, so I won't post a link to an external site yet... but if you search clusterssh, you'll find tutorials and help in relation to it. I feel this would be your best bet.

---

### Post by Sef on 2014-04-12
Check out [Edubuntu]("http://edubuntu.org/"). >  [COLOR=#252525][FONT=Helvetica Neue]Included with Edubuntu is the [/FONT][/COLOR][Linux Terminal Server Project]("https://en.wikipedia.org/wiki/Linux_Terminal_Server_Project") Quote is from [Wikipedia]("https://en.wikipedia.org/wiki/Edubuntu").

---

### Post by wiliam2 on 2014-04-14
Thanks guys! We will study all solutions proposed.
In the end of the process I will try post some conclusion.

---

