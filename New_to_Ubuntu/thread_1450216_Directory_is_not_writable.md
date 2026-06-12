---
title: "Directory is not writable"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by souraklis on 2010-04-08
hello there. I m trying to install matlab. During the installation when it asked me to verify the the installation directory name i have this message:
Directory /usr/local/matlab is not writeable. I tried this code 

path = /usr/local/matlab
writeable = Yes

but nothing
Can anyone help me??
thanks in andance..

---

### Post by gmargo on 2010-04-08
Run the installation with the **sudo** command before it.

---

### Post by souraklis on 2010-04-09
Ok as I dont know much in installation progress in ubuntu i ve an installer that i must install so i gave the path /media/cdrom0 of the cdrom and after that i tried the command ./install. But i had this message "command not found".

---

### Post by gmargo on 2010-04-09
Try
```

cd /media/cdrom0
sudo ./install

```

---

### Post by souraklis on 2010-04-09
Ok i forgot that before i had the same message when i tried with sudo.

---

### Post by Jeanke on 2010-04-09
Are you sure you received 'command not found' and not 'no such file or directory' after you entered ./install?

---

### Post by souraklis on 2010-04-09
When i used sudo the message was command not found
 but when i used the command without sudo i received No such file or directory

---

### Post by Jeanke on 2010-04-09
ok, can you check which files are exactly on the cd?
you can find by:
```
cd /media/cdrom0
ls
```

---

### Post by souraklis on 2010-04-09
ok thank you i find it but now i ve got new problem :( i havent moved propelry the licence so in the installation i received the message installation failed THE THW_archive licence checkout failed.
My qustion is how can i trasfer a file properly?

---

### Post by Jeanke on 2010-04-09
Not sure about that one... Never worked with Matlab.

Maybe one of following can help:
[http://www.mathworks.com/support/solutions/en/data/1-15QSL/index.html?solution=1-15QSL]("http://www.mathworks.com/support/solutions/en/data/1-15QSL/index.html?solution=1-15QSL")
[https://help.ubuntu.com/community/MATLAB]("https://help.ubuntu.com/community/MATLAB")
[http://linux.dsplabs.com.au/forums/ubuntu-linux-help/matlab-on-ubuntu-t8.html]("http://linux.dsplabs.com.au/forums/ubuntu-linux-help/matlab-on-ubuntu-t8.html")

---

### Post by souraklis on 2010-04-09
In the cd there is a file licence_locked.dat but it asked for me licence.dat and I move the licence_locked.dat believing as is the only dat file in the cd. Maybe i have to change something here

```
# MATLAB license passcode file for use with FLEXnet.
SERVER zenitis-laptop***********************************
DAEMON MLM /usr/local/matlab75/etc/licence.dat
INCREMENT TMW_Archive             MLM 16 01-jan-1999   0 0123456789ABCDEFGHIJ VENDOR_STRING="81" HOSTID=0016d48a4f98
INCREMENT MATLAB_Distrib_Comp_Engine MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT MATLAB                  MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT SIMULINK                MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Aerospace_Blockset      MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Aerospace_Toolbox       MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Bioinformatics_Toolbox  MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Communication_Blocks    MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Communication_Toolbox   MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Control_Toolbox         MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Curve_Fitting_Toolbox   MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Database_Toolbox        MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Distrib_Computing_Toolbox MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Extend_Symbolic_Toolbox MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Filter_Design_HDL_Coder MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Filter_Design_Toolbox   MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Fin_Derivatives_Toolbox MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Financial_Toolbox       MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Fixed_Income_Toolbox    MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Fixed_Point_Toolbox     MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Fuzzy_Toolbox           MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Garch_Toolbox           MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT GADS_Toolbox            MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Image_Toolbox           MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Instr_Control_Toolbox   MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Link_for_Incisive       MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Link_for_ModelSim       MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT MAP_Toolbox             MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT MATLAB_Builder_for_Java MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Compiler                MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT MATLAB_Report_Gen       MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT MPC_Toolbox             MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Neural_Network_Toolbox  MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Optimization_Toolbox    MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT PDE_Toolbox             MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Real-Time_Workshop      MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT RTW_Embedded_Coder      MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT RF_Blockset             MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT RF_Toolbox              MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Robust_Toolbox          MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Signal_Blocks           MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Signal_Toolbox          MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT SimBiology              MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Simscape                MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT SimDriveline            MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT SimEvents               MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT SimHydraulics           MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT SimMechanics            MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Power_System_Blocks     MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Simulink_Control_Design MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Simulink_Design_Verifier MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Fixed-Point_Blocks      MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Simulink_HDL_Coder      MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Simulink_Param_Estimation MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT SIMULINK_Report_Gen     MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT NCD_Toolbox             MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT SL_Verification_Validation MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Spline_Toolbox          MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Stateflow               MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Stateflow_Coder         MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Statistics_Toolbox      MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Symbolic_Toolbox        MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Identification_Toolbox  MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT SystemTest              MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Video_and_Image_Blockset MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Virtual_Reality_Toolbox MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""
INCREMENT Wavelet_Toolbox         MLM 16 01-jan-1999   1 0123456789ABCDEFGHIJ ""

```

---

### Post by souraklis on 2010-04-10
Ok finally i ve managed to install it with your help(thanks a lot) know i got this message when i tried to run it

```
License checkout failed.
License Manager Error -95
MATLAB is unable to connect to the license server. 
Make sure you can resolve the hostname of your machine. 
If you are unable to resolve the hostname, contact your System Administrator.

Troubleshoot this issue by visiting: 
http://www.mathworks.com/support/lme95b

Diagnostic Information:
Feature: MATLAB 
License path: /usr/local/matlab75/etc/license.dat:/usr/local/matlab75/etc/*.lic: 
FLEXnet Licensing error: -95,378. System Error: 115

```

---

### Post by gmargo on 2010-04-10
If a licensing daemon was installed, perhaps it was not activated at that time, so try a reboot.  If that doesn't work, you'll have to ask the matlab people.

---

### Post by souraklis on 2010-04-10
I found this
> Ok, got it. Just needed to:
1. Add the following line (before the first uncommented one) to Matlabdir/bin/matlab


export AWT_TOOLKIT=MToolkit

to
2. Launch matlab

matlab -desktop

It runs from the Launch app menu (Alt+F2).

If that doesn't work for you then you may need to do rename a java directory in the MatLab install.

Hope that helps.

so i have a shellscript file and i need to open it and put this line how can i have access to shellscript file???

---

### Post by souraklis on 2010-04-11
i did what it said here [http://ubuntuforums.org/archive/index.php/t-627897.html](http://ubuntuforums.org/archive/index.php/t-627897.html) I added the lines in the matlab file but i have the same problem.

---

### Post by souraklis on 2010-04-20
ok the case is that the licence.dat that i ve in the cd is not the wright one. I ve just downloaded another licence.dat and that's all the problem is solved. Thank you a lot from your help. The only thing that i want to ask in the end is a silly question i want to make an icon of matlab in the desktop (as in the windows). How can I do such thing??

---

### Post by achase79 on 2010-04-20
if you have a link in the menu, you can drag it to the desktop. Otherwise you will have to create a launcher on the desktop by right clicking on the Desktop and choosing create launcher and filling in the correct info.

---

### Post by souraklis on 2010-04-20
I want to thank everybody from your appreciable help. Until today i ve been using XP only because of Matlab now i can devote myself to linux.

---

