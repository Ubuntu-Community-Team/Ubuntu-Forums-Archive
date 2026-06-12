---
title: "Easy user to change Plymouth boot splash"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by willmsbrt1 on 2011-03-09
Customizing Plymouth boot screen to one of your choice 

Start with adding nautilus file browser to system tools 

Right click Gnome Start Menu/Edit Menus/System Tools/New Item/Application in Terminal 
 

 Command : gksu nautilus ( nautilus ) root access to files
 Run this command in terminal 

sudo apt-get install plymouth-theme-*
Note : This will install  the plymouth themes in the repository.
Next, select the theme that you want to display:
Select Plymouth Splash  
Run in terminal
sudo update-alternatives --config default.plymouth
and select xubuntu-logo 
Run in Terminal
sudo update-initramfs -u 
Open Nautilus ( Applications>System Tools>Nautilus ( if added from previous steps , or gksu nautilus in terminal)
Select File System > lib > plymouth > themes > xubuntu-logo
You will see the xubuntu-logo .png , copy and paste the .png logo file you desire to use ( must be .png ) to this folder ( rename photo of choice to xubuntu-logo  , select replace when prompted )
Run  sudo update-initramfs -u in terminal again
Restart and you should see your updated splash screen of choice :)

---

