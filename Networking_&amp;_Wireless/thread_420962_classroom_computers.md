---
title: "classroom computers"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by leg on 2007-04-24
Morning,

            I have been asked to look into having a room of computers running Linux that we can use in one of our classrooms. The computers will need to be networked to the Windows "my documents" for students that log on. Programming subjects will be taught in there mostly (C++ & Ogre for now) but Internet access will be needed. It will need to work seemlessly otherwise students will get the wrong impression of our favourite OS. In other words they must be able to access their documents and access Internet. I was toying with the idea of the new Dell machines that are shipping with Ubuntu.

My first thoughts are that NFS, NIS and Samba will need to be used but can any of you point me to some tutorials for doing this or share your experieces.

[edit] - ok just realised Dell are only pre-installing RHEL on their systems. Anyone know where to purchase some fairly decent spec Ubuntu pre-installed computers.

---

### Post by jonallport on 2007-04-24
At a glance, yes you could sort it with NFS & NIS, but it sounds like you already have a Windows infrastructure (running AD?) Samba with Winbind will pull your Linux machines into that, enabling Windoze users accounts on Linux machines, also there are some neat options with Samba/Winbind for user environment integration.

Hope that's a nudge in the right direction.

---

### Post by leg on 2007-04-24
Fantastic that sounds just what I want I will start looking into that.

---

