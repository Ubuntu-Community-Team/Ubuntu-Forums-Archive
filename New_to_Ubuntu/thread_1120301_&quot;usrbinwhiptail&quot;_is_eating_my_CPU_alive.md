---
title: "&quot;/usr/bin/whiptail&quot; is eating my CPU alive"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by Vunutus on 2009-04-08
I got home today to notice that my computer was in an uproar with all fans blowing at maximum speed and the CPU temperature showing that it was running fairly hot.

Puzzled, I poked around a bit and noticed that I left my CPU frequency scaler thing set to not scale back. I figured this had something to do with it so I set it back to normal operation. This, however, did not help the problem.

I ran ps aux and determined that a program called whiptail (/usr/bin/whiptail started by root) is apparently using 96% of my CPU's clock time CONSTANTLY, and has been doing so for 1200 minutes. I googled for what this program was and didn't find any consistent definition.

Does anyone know what this is any why it's taking so much CPU? I haven't tried restarting yet, but even that does make it go away I'd still like to know what it is and what program could possibly use nearly all of my CPU for 1200 minutes without finishing what it was doing.

The only new or out of the ordinary things I did in that timeframe was installing my video driver (after which I restarted, I believe) and messing around with Windows XP inside virtualbox. VirtualBox confirms, however, that no image is currently active.

---

### Post by tommynz1975 on 2009-04-08
this link may or may not be useful to you
[html]http://www.wlug.org.nz/whiptail(1)[/html]**NAME**

 whiptail - display dialog boxes from shell scripts
 **SYNOPSIS**

 **whiptail** _[ __--title__ ''title''_[?]("http://www.wlug.org.nz/%5B%20__--title__%20%27%27title%27%27?action=create") _[ __--backtitle__ ''backtitle''_[?]("http://www.wlug.org.nz/%5B%20__--backtitle__%20%27%27backtitle%27%27?action=create") _[ __--clear___[?]("http://www.wlug.org.nz/%5B%20__--clear__?action=create") _[ __--defaultno___[?]("http://www.wlug.org.nz/%5B%20__--defaultno__?action=create") _[ __--fb___[?]("http://www.wlug.org.nz/%5B%20__--fb__?action=create") _[ __--nocancel___[?]("http://www.wlug.org.nz/%5B%20__--nocancel__?action=create") _[ __--noitem___[?]("http://www.wlug.org.nz/%5B%20__--noitem__?action=create") _[ __--separate-output___[?]("http://www.wlug.org.nz/%5B%20__--separate-output__?action=create") _[ __--scrolltext___[?]("http://www.wlug.org.nz/%5B%20__--scrolltext__?action=create") **box-options**
 **DESCRIPTION**

 **whiptail** is a program that will let you to present a variety of questions or display messages using dialog boxes from a shell script. Currently, these types of dialog boxes are implemented: **yes/no** box, **menu** box, **input** box, **message** box, **text** box, **info** box, **checklist** box, **radiolist** box **gauge** box, and **password** box.
 **OPTIONS**

 **--clear**The screen will be cleared to the **screen attribute** on exit. This doesn't work in an xterm (and descendants) if alternate screen switching is enabled, because in that case slang writes to (and clears) an alternate screen.**--defaultno**The dialog box will open with the cursor over the **No** button.**--fb**Use full buttons. (By default, **whiptail** uses compact buttons).**--nocancel**The dialog box won't have a **Cancel** button.**--noitem**The menu, checklist and radiolist widgets will display tags only, not the item strings.**--separate-output**For checklist widgets, output result one line at a time, with no quoting. This facilitates parsing by another program.**--title** *title*Specifies a *title* string to be displayed at the top of the dialog box.**--backtitle** *backtitle*Specifies a *backtitle* string to be displayed on the backdrop, at the top of the screen.**--scrolltext**Force the display of a vertical scrollbar. **Box Options**
 **--yesno** *text height width*A **yes/no** dialog box of size *height* rows by *width* columns will be displayed. The string specified by *text* is displayed inside the dialog box. If this string is too long to be fitted in one line, it will be automatically divided into multiple lines at appropriate places. The *text* string may also contain the sub-string  or newline characters *`n*' to control line breaking explicitly. This dialog box is useful for asking questions that require the user to answer either yes or no. The dialog box has a **Yes** button and a **No** button, in which the user can switch between by pressing the *TAB* key.**--msgbox** *text height width*A **message** box is very similar to a **yes/no** box. The only difference between a **message** box and a ; **yes/no** box is that a **message** box has only a single **OK** button. You can use this dialog box to display any message you like. After reading the message, the user can press the *ENTER* key so that **whiptail** will exit and the calling shell script can continue its operation.**--infobox** *text height width*An **info** box is basically a **message** box. However, in this case, **whiptail** will exit immediately after displaying the message to the user. The screen is not cleared when **whiptail** exits, so that the message will remain on the screen until the calling shell script clears it later. This is useful when you want to inform the user that some operations are carrying on that may require some time to finish.**--inputbox** *text height width _[init_[?]("http://www.wlug.org.nz/%5Binit?action=create")*An **input** box is useful when you want to ask questions that require the user to input a string as the answer. If init is supplied it is used to initialize the input string. When inputing the string, the *BACKSPACE* key can be used to correct typing errors. If the input string is longer than can be fitted in the dialog box, the input field will be scrolled. On exit, the input string will be printed on *stderr*.**--passwordbox** *text height width _[init_[?]("http://www.wlug.org.nz/%5Binit?action=create")*A **password** box is similar to an input box, except the text the user enters is not displayed. This is useful when prompting for passwords or other sensative information. Be aware that if anything is passed in**--textbox** *file height width*A **text** box lets you display the contents of a text file in a dialog box. It is like a simple text file viewer. The user can move through the file by using the *UP/DOWN*, *PGUP/PGDN* and *HOME/END* keys available on most keyboards. If the lines are too long to be displayed in the box, the *LEFT/RIGHT* keys can be used to scroll the text region horizontally. For more convenience, forward and backward searching functions are also provided.**--menu** *text height width menu-height* _[ ''tag item''_[?]("http://www.wlug.org.nz/%5B%20%27%27tag%20item%27%27?action=create") *...*As its name suggests, a **menu** box is a dialog box that can be used to present a list of choices in the form of a menu for the user to choose. Each menu entry consists of a *tag* string and an *item* string. The *tag* gives the entry a name to distinguish it from the other entries in the menu. The *item* is a short description of the option that the entry represents. The user can move between the menu entries by pressing the *UP/DOWN* keys, the first letter of the *tag* as a hot-key, or the number keys *1-9*. There are *menu-height* entries displayed in the menu at one time, but the menu will be scrolled if there are more entries than that. When ; **whiptail** exits, the *tag* of the chosen menu entry will be printed on *stderr*.**--checklist** *text height width list-height* _[ ''tag item status''_[?]("http://www.wlug.org.nz/%5B%20%27%27tag%20item%20status%27%27?action=create") *...*A **checklist** box is similar to a **menu** box in that there are multiple entries presented in the form of a menu. Instead of choosing one entry among the entries, each entry can be turned on or off by the user. The initial on/off state of each entry is specified by *status*. On exit, a list of the *tag* strings of those entries that are turned on will be printed on *stderr*.**--radiolist** *text height width list-height* _[ ''tag item status''_[?]("http://www.wlug.org.nz/%5B%20%27%27tag%20item%20status%27%27?action=create") *...*A **radiolist** box is similar to a **menu** box. The only difference is that you can indicate which entry is currently selected, by setting its *status* to *on*.**--gauge** *text height width percent*A **gauge** box displays a meter along the bottom of the box. The meter indicates the percentage. New percentages are read from standard input, one integer per line. The meter is updated to reflect each new percentage. If stdin is XXX, then subsequent lines up to another XXX are used for a new prompt. The gauge exits when EOF is reached on stdin. **DIAGNOSTICS**

 Exit status is 0 if **whiptail** is exited by pressing the **Yes** or **OK** button, and 1 if the **No** or **Cancel** button is pressed. Otherwise, if errors occur inside **whiptail** or **whiptail** is exited by pressing the *ESC* key, the exit status is -1.
 **AUTHOR**

 Based on the man page for [dialog(1)]("http://www.wlug.org.nz/dialog%281%29") by:
 Savio Lam (lam836@cs.cuhk.hk) - version 0.3 
Stuart Herbert (S.Herbert@sheffield.ac.uk) - patch for version 0.4
 Modifications for whiptail by: Enrique Zanardi (ezanard@debian.org

---

### Post by Hospadar on 2009-04-08
in short, it shouldn't have been sucking things up and is probably safe to kill, it looks like an xmessage clone, which is designed to get simple input from a user from a shell script.

---

