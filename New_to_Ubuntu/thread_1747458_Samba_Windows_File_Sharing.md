---
title: "Samba Windows File Sharing"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by D_2 on 2011-05-02
I am wanting to do some file sharing through Windows and I have Samba installed and it seems to be working, what I am wanting to do is, when I go through the windows file manager and click on the shared file on my Ubuntu server I want windows to come up with a dialog box asking for my username and password for my server so I can have full access in creating new folders, files, modifying files all of the fun things without having everything in the shared directory with the file mode of 777. I would like to have some kind of security on the files and folders of the system and not have it wide open, so is there a way I can have windows ask me for a username and password when I access any of the shares on the server.

Thanks for any help.

---

### Post by papibe on 2011-05-03
There's a graphical user interface that can help you configure your shares. When you open one of them there will be a tab called Access, there you can restrict the use of the share from everyone to a list of specific users.

Go to the software center and look for Samba, the package itself is called Samba, if you click "More Info", you'll see in the description "system-config-samba".

I hope it helps.

---

