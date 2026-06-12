---
title: "Right Mouse Button menu error."
date: 2010-05-04
forum: New to Ubuntu
---

### Post by brlisandro on 2010-05-04
Thanks to this forum and other web tutorials I have a changed ubuntu looks with Emerald, Compiz, Metecity, gconf-editor, etc.  But when all was perfect the mouse right button menu had a little error. 

When I click the second button in any application It choses the first option. I have to keep it pressed so i can choose the option I need. 

I want to just click. The Menu appears and then click on the option. 

Example. Application GEDIT. Write a word. Right mouse button click It choses "UNDO" which is the first option. I have do keep it pressed so I can chose another option. Same on chromium. 

Maybe it easy, but i Couldn't find the solution anywhere.

Thank you. 

[B]UBUNTU L.L. 10.04 GNOME COMPIZ EMERALD
[/B]

---

### Post by mechro on 2010-05-04
I had a similar problem when I had my mouse unnecessarily configured in my xorg.conf file. Please post your /etc/X11/xorg.conf file.

---

### Post by brlisandro on 2010-05-04
Thats fast. On UBUNTU 10.04 is just


```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by mechro on 2010-05-04
Well that's exactly the same as my current "mouseless "xorg.conf so it's not that causing your problem.

Try running without 3D Visual Effects (Compiz) and see if that solves the problem.

---

### Post by brlisandro on 2010-05-04
Nope. Copiz off, problem remains. 
Tried with Emerald off. Metacity on. and vice versa. Nothing.

Thank you for the fast response.

---

### Post by warfacegod on 2010-05-04
Try poking around in Assistive Technologies and Mouse. It sounds like you have some secondary function set up.

---

### Post by brlisandro on 2010-05-05
I'll l search for Mouse options in Ubuntu Tweak and some others. 
At the menu

Ubuntu Tweak
Desktop --> Windows Manager Settings. 
It has several options regarding the mouse buttons. I just choosed "none" on the "righ button" option. But nothing happened. 

I'll keep looking. Thank you for the support to both of you.

---

### Post by warfacegod on 2010-05-05
System> Preferences> Mouse> Accessibility might be a good place to look.

---

### Post by arpanaut on 2010-05-05
**Bug or Feature?** :p

It's been an irritation to me for some time, but like the buttons on the left, I've gotten used to it. I've adapted. 
In fact now when in windows, and I right click-hold-move to selection-release and it doesn't select I am puzzled.;)

Funny how that works!

---

### Post by mechro on 2010-05-05
This behaviour does depend on your theme.

For example the Human theme always highlights an item in a context menu whereas something like Traditional doesn't. If you don't release the mouse quick enough on a highlighted item it will perform that action.

I can't find a way to configure the mouse position on opening a context menu or to alter the speed at which it'll register as a click.

Try a different theme as a test and maybe someone can figure out how to add extra "padding" in the context menus of your current theme.

---

### Post by brlisandro on 2010-05-05
SOLVED 

You were right, changing the Theme fix this problem. I have to customize this new theme so it like the other but without this configuration or change the padding, as I was told here (thank you for that). 


I edited the theme file

[FONT="Arial Narrow"]home/"username"/.themes/"theme_name"/gtk-2.0/gtkrc[/FONT]

**Edit some menus paddings to "10"**. Some of them have to be "0", otherwise it will mess all up. 

```
style "moomex-pixmap" {
  [B]GtkMenu        ::horizontal_padding   = 10
  GtkMenu        ::vertical_padding     = 10[/B]
  WnckTasklist   ::fade-overlay-rect 	= 0
  GtkRange       ::trough_border    	= 0
  GtkRange       ::slider_width      	= 15
  GtkRange       ::stepper_size      	= 15
  GtkPaned       ::handle_size       	= 6
  **GtkToolbar     ::internal-padding  	= 0**
  GtkScrollbar   ::min_slider_length 	= 30
  **GtkMenuBar     ::internal-padding  	= 0**
  GtkExpander    ::expander_size     	= 16
  GtkScale       ::slider-length     	= 15
  GtkTreeView    ::expander_size     	= 14
  GtkWidget	 ::interior_focus	= 1
  GtkWidget	 ::focus_padding	= 0
  GtkCheckButton ::indicator_size    	= 12
  GtkButton      ::child-displacement-x = 0
  GtkButton      ::child-displacement-y = 0
  GtkButton      ::default_border    	= { 0, 0, 0, 0 }
  GtkButton	 ::inner-border 	= { 3, 3, 0, 0 }
  GtkButton	 ::outside-border	= { 0, 0, 0, 0 }
  GtkEntry	 ::inner-border		= { 1, 1, 1, 1 }
  GtkTreeView	 ::odd_row_color     	= @base_color
  GtkTreeView	 ::even_row_color    	= shade (1.0, @base_color


```

[COLOR="Orange"][SIZE="5"]Thank you all[/SIZE][/COLOR]

---

### Post by mechro on 2010-05-06
> **brlisandro said:**
> SOLVED 

You were right, changing the Theme fix this problem. I have to customize this new theme so it like the other but without this configuration or change the padding, as I was told here (thank you for that). 


I edited the theme file

[FONT="Arial Narrow"]home/"username"/.themes/"theme_name"/gtk-2.0/gtkrc[/FONT]

**Edit some menus paddings to "10"**. Some of them have to be "0", otherwise it will mess all up. 

```
style "moomex-pixmap" {
  [B]GtkMenu        ::horizontal_padding   = 10
  GtkMenu        ::vertical_padding     = 10[/B]
  WnckTasklist   ::fade-overlay-rect 	= 0
  GtkRange       ::trough_border    	= 0
  GtkRange       ::slider_width      	= 15
  GtkRange       ::stepper_size      	= 15
  GtkPaned       ::handle_size       	= 6
  **GtkToolbar     ::internal-padding  	= 0**
  GtkScrollbar   ::min_slider_length 	= 30
  **GtkMenuBar     ::internal-padding  	= 0**
  GtkExpander    ::expander_size     	= 16
  GtkScale       ::slider-length     	= 15
  GtkTreeView    ::expander_size     	= 14
  GtkWidget	 ::interior_focus	= 1
  GtkWidget	 ::focus_padding	= 0
  GtkCheckButton ::indicator_size    	= 12
  GtkButton      ::child-displacement-x = 0
  GtkButton      ::child-displacement-y = 0
  GtkButton      ::default_border    	= { 0, 0, 0, 0 }
  GtkButton	 ::inner-border 	= { 3, 3, 0, 0 }
  GtkButton	 ::outside-border	= { 0, 0, 0, 0 }
  GtkEntry	 ::inner-border		= { 1, 1, 1, 1 }
  GtkTreeView	 ::odd_row_color     	= @base_color
  GtkTreeView	 ::even_row_color    	= shade (1.0, @base_color


```

[COLOR="Orange"][SIZE="5"]Thank you all[/SIZE][/COLOR]

Wow! you worked out the settings to change in your theme. I'm gonna have a go at that with my Human theme. Thanks. :grin:

---

