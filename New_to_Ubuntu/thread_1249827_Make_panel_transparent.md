---
title: "Make panel transparent"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Zopiac on 2009-08-25
With my current theme, Black Rain (found it on gnome-look.org), I cannot get my gnome-panel to be transparent. Attached I have screenshots of my desktop with the panel background being the theme default (which doesn't work with my vertical panel, but I can fix that) and with it being a solid colour with transparency. With the latter, however, the Dockbar Applet doesn't become transparent; it just uses the same theme default as before.

The gtkrc shows that is uses the pixmap engine (I think, I just skimmed through it and don't know much about this); perhaps pixmaps don't allow transparency? I tried editing a few files in its ~/.themes folder but nothing worked.

Here's a copy of the gtkrc:
```
#MK64
# Set GtkSettings color scheme property.
# This can be overriden (via an xsetting) with eg. the gnome-appearance-properties.
gtk_color_scheme = "fg_color:#d7d7d7\nbg_color:#000000\nbase_color:#0E0E0E\ntext_color:#d7d7d7\nselected_bg_color:#080808\nselected_fg_color:#d7d7d7\ntooltip_bg_color:#d7d7d7\ntooltip_fg_color:#000000"

include "panel.rc"

gtk-icon-sizes = "panel-menu=12,12:panel=16,16:gtk-button=18,18:gtk-large-toolbar=20,20"

gtk-button-images = 0

style "default"
{
	########
	# Style Properties
	########

	GtkButton      ::default_border    		= { 1, 1, 1, 1 }
	GtkButton      ::default_outside_border    	= { 1, 1, 1, 1 }
	GtkButton      ::child-displacement-x = 1
	GtkButton      ::child-displacement-y = 1
	GtkCheckButton ::indicator-size       = 14
	GtkWidget      ::focus_padding			= 0
	GtkProgressBar ::trough_border			= 0

	GtkPaned       ::handle-size          = 6

	GtkRange       ::trough-border        = 0
	GtkRange       ::slider-width         = 15
	GtkRange       ::stepper-size         = 15

	GtkScale       ::slider-length        = 31
	#GtkScale       ::trough-side-details  = 1
	GtkScrollbar   ::min-slider-length    = 40

	GtkMenuBar     ::internal-padding     = 0

	#GtkToolbar     ::internal-padding     = 1


	#GtkMenu        ::horizontal-padding   = 0
	#GtkMenu        ::vertical-padding     = 0

	GtkTreeView    ::expander_size     		= 8
	GtkExpander    ::expander_size     		= 8

	# Glow the tasklist by changing the color, instead of overlaying it with a rectangle
	WnckTasklist   ::fade-overlay-rect    = 0
	GtkStatusbar     ::shadow-type       	= GTK_SHADOW_NONE

	#xthickness = 1
	#ythickness = 1

	GtkEntry::cursor_color = @text_color
	GtkTextView::cursor_color = @text_color
	GtkWidget::cursor_color = @text_color



	fg[NORMAL]        = @fg_color
	fg[PRELIGHT]      = shade (1.20, @fg_color)
	fg[SELECTED]      = @selected_fg_color
	fg[ACTIVE]        = shade (0.9, @fg_color)
	fg[INSENSITIVE]   = shade (0.4, @fg_color)

	bg[NORMAL]        = @bg_color
	bg[PRELIGHT]      = shade (1.20,  @bg_color)
	bg[SELECTED]	  = @selected_bg_color
	bg[INSENSITIVE]   = @bg_color
	bg[ACTIVE]        = shade (0.9, @bg_color)

	# window background
	#bg_pixmap[NORMAL] = "/shadows/window-bg.png"

	base[NORMAL]      = @base_color
	base[PRELIGHT]    = shade (1.20,  @bg_color)
	base[ACTIVE]      = shade (0.7, @selected_bg_color)
	base[SELECTED]    = shade (0.9, @selected_bg_color)
	base[INSENSITIVE] = shade (0.40, @base_color)

	text[NORMAL]      = @text_color
	text[PRELIGHT]    = shade (1.20, @text_color)
	text[ACTIVE]      = @selected_fg_color
	text[SELECTED]    = @selected_fg_color
	text[INSENSITIVE] = shade (0.40, @text_color)



	engine "clearlooks" 
	{
		colorize_scrollbar = TRUE
		menubarstyle      = 2      # 0 = flat, 1 = sunken, 2 = flat gradient
		toolbarstyle      = 0      # 0 = flat, 1 = enable effects
		animation         = TRUE
		style             = GLOSSY
		hint		  = "use-hints" # Set a hint to disable backward compatibility fallbacks.
	}

engine "pixmap"
{
	image
	{
		function	= HANDLE
		recolorable	= TRUE
		overlay_file	= "/handles/handle-v.png"
		overlay_stretch	= FALSE
		orientation	= VERTICAL
	}

	image
	{
		function	= HANDLE
		recolorable	= TRUE
		overlay_file	= "/handles/handle-h.png"
		overlay_stretch	= FALSE
		orientation	= HORIZONTAL
	}

	image
	{
		function	= ARROW
		recolorable	= TRUE
		overlay_file	= "/arrows/arrow-up.png"
		overlay_border	= {2,2,2,2}
		overlay_stretch	= FALSE
		arrow_direction	= UP
	}

	image
	{
		function	= ARROW
		recolorable	= TRUE
		overlay_file	= "/arrows/arrow-down.png"
		overlay_border	= {2,2,2,2}
		overlay_stretch	= FALSE
		arrow_direction	= DOWN
	}

	image
	{
		function	= ARROW
		recolorable	= TRUE
		overlay_file	= "/arrows/arrow-left.png"
		overlay_border	= {2,2,2,2}
		overlay_stretch	= FALSE
		arrow_direction	= LEFT
	}

	image
	{
		function	= ARROW
		recolorable	= TRUE
		overlay_file	= "/arrows/arrow-right.png"
		overlay_border	= {2,2,2,2}
		overlay_stretch	= FALSE
		arrow_direction	= RIGHT
	}

	image
	{
		function	= VLINE
		recolorable	= TRUE
		file		= "/lines/line-v.png"
		border		= {0,0,0,0}
		stretch		= TRUE
		}

	image
	{
		function	= HLINE
		recolorable	= TRUE
		file		= "/lines/line-h.png"
		border		= {0,0,0,0}
		stretch		= TRUE
		}


	image
	{
		function	= SHADOW
		shadow		= IN
		recolorable	= FALSE
		file		= "/shadows/shadow-in.png"
		border		= {1,1,1,1}
		stretch		= TRUE
		}

	image
	{
		function	= SHADOW
		shadow		= OUT
		recolorable	= TRUE
		file		= "/shadows/shadow-in.png"
		border		= {1,1,1,1}
		stretch		= TRUE
		}

	image
	{
		function	= SHADOW
		shadow		= ETCHED_IN
		recolorable	= TRUE
		file		= "/shadows/frame1.png"
		border		= {1,1,1,1}
		stretch		= TRUE
		}

	image
	{
		function	= SHADOW
		shadow		= ETCHED_OUT
		recolorable	= TRUE
		file		= "/shadows/shadow-none.png"
		border		= {1,1,1,1}
		stretch		= TRUE
		}

	image
	{
		function	= SHADOW_GAP
		recolorable	= TRUE
		file		= "/shadows/frame1.png"
		border		= {1,1,1,1}
		stretch		= TRUE
		gap_start_file	= "/shadows/shadow-none.png"
		gap_start_border= { 1 , 1 ,1 ,1}
		gap_start_file	= "/shadows/shadow-none.png"
		gap_start_border= { 1 , 1 ,1 ,1}
		gap_side	= TOP
		
		}

	image
	{
		function	= FOCUS
		recolorable	= TRUE
		file		= "/other/focus.png"
		border		= {5,5,5,5}
		stretch		= TRUE
		}


}

}

style "scrollbars" = "default"
{
engine "pixmap"
{

	image
	{
		function	= BOX
		recolorable	= TRUE
		detail		= "trough"
		file		= "/scrollbar/trough-scrollbar-horiz.png"
		border		= { 30 , 30 , 0 , 0 }
		stretch		= TRUE
		orientation	= HORIZONTAL
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		detail		= "trough"
		file		= "/scrollbar/trough-scrollbar-vert.png"
		border		= { 0 , 0 , 30 , 30 }
		stretch		= TRUE
		orientation	= VERTICAL
	}

	image
	{
		function	= SLIDER
		recolorable	= TRUE
		state		= NORMAL
		file		= "/scrollbar/slider-horiz.png"
		border		= { 4 , 4 , 2 , 2 }
		stretch		= TRUE
		orientation	= HORIZONTAL
		
	}

	image
	{
		function	= SLIDER
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/scrollbar/slider-horiz-prelight.png"
		border		= {4 , 4 , 2 , 2 }
		stretch		= TRUE
		orientation	= HORIZONTAL
		
	}

	image
	{
		function	= SLIDER
		recolorable	= TRUE
		state		= ACTIVE
		file		= "/scrollbar/slider-horiz-prelight.png"
		border		= {4 , 4  , 2 , 2 }
		stretch		= TRUE
		orientation	= HORIZONTAL
		
	}

	image
	{
		function	= SLIDER
		recolorable	= TRUE
		state		= INSENSITIVE
		file		= "/scrollbar/slider-horiz-prelight.png"
		border		= {4 , 4  , 2 , 2 }
		stretch		= TRUE
		orientation	= HORIZONTAL
		
	}

	image
	{
		function	= SLIDER
		recolorable	= TRUE
		state		= NORMAL
		file		= "/scrollbar/slider-vert.png"
		border		= { 2 , 2 , 4 , 4  }
		stretch		= TRUE
		orientation	= VERTICAL
		
	}

	image
	{
		function	= SLIDER
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/scrollbar/slider-vert-prelight.png"
		border		= { 2 , 2 , 4 , 4  }
		stretch		= TRUE
		orientation	= VERTICAL
		
	}

	image
	{
		function	= SLIDER
		recolorable	= TRUE
		state		= ACTIVE
		file		= "/scrollbar/slider-vert-prelight.png"
		border		= { 2 , 2 , 4 , 4  }
		stretch		= TRUE
		orientation	= VERTICAL
		
	}

	image
	{
		function	= SLIDER
		recolorable	= TRUE
		state		= INSENSITIVE
		file		= "/scrollbar/slider-vert-prelight.png"
		border		= { 2 , 2 , 4 , 4  }
		stretch		= TRUE
		orientation	= VERTICAL
		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= NORMAL
		file		= "/scrollbar/stepper-up.png"
		stretch		= TRUE
		arrow_direction	= UP

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/scrollbar/stepper-up-prelight.png"
		stretch		= TRUE
		arrow_direction	= UP

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= ACTIVE
		file		= "/scrollbar/stepper-up-prelight.png"
		stretch		= TRUE
		arrow_direction	= UP

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= INSENSITIVE
		file		= "/scrollbar/stepper-up.png"
		stretch		= TRUE
		arrow_direction	= UP

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= NORMAL
		file		= "/scrollbar/stepper-down.png"
		stretch		= TRUE
		arrow_direction	= DOWN

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/scrollbar/stepper-down-prelight.png"
		stretch		= TRUE
		arrow_direction	= DOWN

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= ACTIVE
		file		= "/scrollbar/stepper-down-prelight.png"
		stretch		= TRUE
		arrow_direction	= DOWN

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= INSENSITIVE
		file		= "/scrollbar/stepper-down.png"
		stretch		= TRUE
		arrow_direction	= DOWN

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= NORMAL
		file		= "/scrollbar/stepper-left.png"
		stretch		= TRUE
		arrow_direction	= LEFT

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/scrollbar/stepper-left-prelight.png"
		stretch		= TRUE
		arrow_direction	= LEFT

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= ACTIVE
		file		= "/scrollbar/stepper-left-prelight.png"
		stretch		= TRUE
		arrow_direction	= LEFT

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= INSENSITIVE
		file		= "/scrollbar/stepper-left.png"
		stretch		= TRUE
		arrow_direction	= LEFT

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= NORMAL
		file		= "/scrollbar/stepper-right.png"
		stretch		= TRUE
		arrow_direction	= RIGHT

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/scrollbar/stepper-right-prelight.png"
		stretch		= TRUE
		arrow_direction	= RIGHT

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= ACTIVE
		file		= "/scrollbar/stepper-right-prelight.png"
		stretch		= TRUE
		arrow_direction	= RIGHT

		
	}

	image
	{
		function	= STEPPER
		recolorable	= TRUE
		state		= INSENSITIVE
		file		= "/scrollbar/stepper-right.png"
		stretch		= TRUE
		arrow_direction	= RIGHT

		
	}

}

}

style "radiobutton-menu"
{
engine "pixmap"
{

	image
	{

		function	= OPTION
		state		= NORMAL
		shadow		= OUT
		overlay_file	= "/check-radio/option1.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		state		= PRELIGHT
		shadow		= OUT
		overlay_file	= "/check-radio/option3.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		state		= ACTIVE
		shadow		= OUT
		overlay_file	= "/check-radio/option1.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		state		= INSENSITIVE
		shadow		= OUT
		overlay_file	= "/check-radio/option5.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		recolorable	= TRUE
		state		= NORMAL
		shadow		= IN
		overlay_file	= "/check-radio/option2.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		recolorable	= TRUE
		state		= PRELIGHT
		shadow		= IN
		overlay_file	= "/check-radio/option4.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		recolorable	= TRUE
		state		= ACTIVE
		shadow		= IN
		overlay_file	= "/check-radio/option4.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		recolorable	= TRUE
		state		= INSENSITIVE
		shadow		= IN
		overlay_file	= "/check-radio/option6.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= FLAT_BOX
		recolorable	= TRUE
		shadow		= IN
		file		= "/check-radio/checklight.png"
		border		= { 2 ,2 , 2 ,2}
		stretch		= TRUE
	}
}
}

style "radiobutton"
{


engine "pixmap"
{

	image
	{

		function	= OPTION
		state		= NORMAL
		shadow		= OUT
		overlay_file	= "/cherad/option1.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		state		= PRELIGHT
		shadow		= OUT
		overlay_file	= "/cherad/option3.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		state		= ACTIVE
		shadow		= OUT
		overlay_file	= "/cherad/option1.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		state		= INSENSITIVE
		shadow		= OUT
		overlay_file	= "/cherad/option5.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		recolorable	= TRUE
		state		= NORMAL
		shadow		= IN
		overlay_file	= "/cherad/option2.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		recolorable	= TRUE
		state		= PRELIGHT
		shadow		= IN
		overlay_file	= "/cherad/option4.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		recolorable	= TRUE
		state		= ACTIVE
		shadow		= IN
		overlay_file	= "/cherad/option4.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= OPTION
		recolorable	= TRUE
		state		= INSENSITIVE
		shadow		= IN
		overlay_file	= "/cherad/option6.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= FLAT_BOX
		recolorable	= TRUE
		shadow		= IN
		file		= "/cherad/checklight.png"
		border		= { 2 ,2 , 2 ,2}
		stretch		= TRUE
	}
}
}

style "checkbutton-menu"
{
engine "pixmap"
{

	image
	{

		function	= CHECK
		state		= NORMAL
		shadow		= OUT
		overlay_file	= "/check-radio/check1.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		state		= PRELIGHT
		shadow		= OUT
		overlay_file	= "/check-radio/check3.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		state		= ACTIVE
		shadow		= OUT
		overlay_file	= "/check-radio/check1.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		state		= INSENSITIVE
		shadow		= OUT
		overlay_file	= "/check-radio/check5.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		recolorable	= TRUE
		state		= NORMAL
		shadow		= IN
		overlay_file	= "/check-radio/check2.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		recolorable	= TRUE
		state		= PRELIGHT
		shadow		= IN
		overlay_file	= "/check-radio/check4.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		recolorable	= TRUE
		state		= ACTIVE
		shadow		= IN
		overlay_file	= "/check-radio/check4.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		recolorable	= TRUE
		state		= INSENSITIVE
		shadow		= IN
		overlay_file	= "/check-radio/check6.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= FLAT_BOX
		recolorable	= TRUE
		shadow		= IN
		file		= "/check-radio/checklight.png"
		border		= { 2 ,2 , 2 ,2}
		stretch		= TRUE
	}
}
}

style "checkbutton"
{


engine "pixmap"
{

	image
	{

		function	= CHECK
		state		= NORMAL
		shadow		= OUT
		overlay_file	= "/cherad/check1.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		state		= PRELIGHT
		shadow		= OUT
		overlay_file	= "/cherad/check3.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		state		= ACTIVE
		shadow		= OUT
		overlay_file	= "/cherad/check1.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		state		= INSENSITIVE
		shadow		= OUT
		overlay_file	= "/cherad/check5.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		recolorable	= TRUE
		state		= NORMAL
		shadow		= IN
		overlay_file	= "/cherad/check2.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		recolorable	= TRUE
		state		= PRELIGHT
		shadow		= IN
		overlay_file	= "/cherad/check4.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		recolorable	= TRUE
		state		= ACTIVE
		shadow		= IN
		overlay_file	= "/cherad/check4.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= CHECK
		recolorable	= TRUE
		state		= INSENSITIVE
		shadow		= IN
		overlay_file	= "/cherad/check6.png"
		overlay_stretch	= FALSE
	}

	image
	{

		function	= FLAT_BOX
		recolorable	= TRUE
		shadow		= IN
		file		= "/cherad/checklight.png"
		border		= { 2 ,2 , 2 ,2}
		stretch		= TRUE
	}
}
}
style "menubar"
{
fg[PRELIGHT] = "#ffffff"
fg[ACTIVE] = "#ffffff"
text[PRELIGHT] = "#ffffff"
text[ACTIVE] = "#ffffff"


xthickness = 0
ythickness = 2


engine "pixmap"
{

	image
	{
		function	= BOX
		state		= NORMAL
		file		= "/menubar/menubar.png"
		border		= { 2 ,2 , 2 ,2}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/menubar/menubar-item.png"
		border		= { 2 ,2 , 2 ,2}
		stretch		= TRUE
	}

}

}

style "menu" = "default"
{

xthickness = 2
ythickness = 2

#bg[NORMAL] = "#353535"
#bg[SELECTED] = "#FFFFFF"
#bg[PRELIGHT] = "#000000"
text[NORMAL] = "#d7d7d7"
text[PRELIGHT] = "#FFFFFF"
text[ACTIVE] = "#FFFFFF"
fg[NORMAL] = "#d7d7d7"
fg[PRELIGHT] = "#ffffff"
fg[ACTIVE] = "#ffffff"


engine "pixmap"
{

	image
	{
		function	= BOX
		recolorable	= TRUE
		detail		= "menu"
		file		= "/menu/menu.png"
		border		= { 28 ,2 , 2 ,2}
		stretch		= TRUE
	}


}
}

style "menuitem"
{

xthickness = 2
ythickness = 4

fg[NORMAL] = "#d7d7d7"
fg[PRELIGHT] = "#ffffff"
fg[ACTIVE] = "#ffffff"
fg[SELECTED] = "#ffffff"
fg[INSENSITIVE] = "#6b6b6b"

text[PRELIGHT] = "#d7d7d7"
text[NORMAL] = "#d7d7d7"
text [ACTIVE] = "#d7d7d7"

base[PRELIGHT] = "#d7d7d7"
base[NORMAL] = "#d7d7d7"

bg[NORMAL] = "#d7d7d7"
bg [SELECTED] = "#000000"



engine "pixmap"
{

	image
	{
		function	= BOX
		recolorable	= TRUE
		file		= "/menu/menuitem.png"
		border		= { 2 ,2 , 2 ,2}
		stretch		= TRUE
	}

}

}

style "optionmenu" = "default"
{

	text[NORMAL]        = @fg_color
	text[PRELIGHT]      = shade (1.20, @fg_color)
	text[SELECTED]      = @selected_fg_color
	text[ACTIVE]        = shade (0.9, @fg_color)
	text[INSENSITIVE]   = shade (0.4, @fg_color)

engine "pixmap"
{

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= NORMAL
		file		= "/button/button-normal.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/button/button-prelight.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= ACTIVE
		file		= "/button/button-prelight.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= INSENSITIVE
		file		= "/button/button-inactive.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= TAB
		recolorable	= TRUE
		state		= NORMAL
		overlay_file	= "/arrows/arrow-down.png"
		overlay_stretch	= FALSE
	}

	image
	{
		function	= TAB
		recolorable	= TRUE
		state		= INSENSITIVE
		overlay_file	= "/arrows/arrow-down.png"
		overlay_stretch	= FALSE
	}

	image
	{
		function	= TAB
		recolorable	= TRUE
		state		= PRELIGHT
		overlay_file	= "/arrows/arrow-down.png"
		overlay_stretch	= FALSE
	}



}

}

style "button" = "default"
{

engine "pixmap"
{

	image
	{
		function	= BOX
		recolorable	= TRUE
		detail		= "buttondefault"
		file		= "/button/button-default.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		state		= NORMAL
		file		= "/button/button-normal.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= PRELIGHT
		shadow		= OUT
		file		= "/button/button-prelight.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= PRELIGHT
		shadow		= IN
		file		= "/button/button-active-prelight.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		state		= INSENSITIVE
		file		= "/button/button-inactive.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}


	image
	{
		function	= BOX
		state		= ACTIVE
		file		= "/button/button-active.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}


}

}

style "listheader"
{

engine "pixmap"
{

	image
	{
		function	= BOX
		state		= NORMAL
		recolorable	= TRUE
		file		= "/listheaders/list-header.png"
		border		= { 2 ,2, 2, 2}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		state		= PRELIGHT
		recolorable	= TRUE
		file		= "/listheaders/list-header-prelight.png"
		border		= { 2 ,2, 2, 2}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		state		= ACTIVE
		recolorable	= TRUE
		file		= "/listheaders/list-header-active.png"
		border		= { 2 ,2, 2, 2}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		state		= INSENSITIVE
		recolorable	= TRUE
		file		= "/listheaders/list-header.png"
		border		= { 2 ,2, 2, 2}
		stretch		= TRUE
	}

}

}

style "toolbutton" = "default"
{
xthickness = 1
ythickness = 0
engine "pixmap"
{

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= NORMAL
		file		= "/toolbar/button-toolbar-normal.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		shadow		= OUT
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/toolbar/button-toolbar-prelight.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		shadow		= IN
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/toolbar/button-toolbar-active-prelight.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= INSENSITIVE
		file		= "/toolbar/button-toolbar-inactive.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= ACTIVE
		file		= "/toolbar/button-toolbar-active.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= ARROW
		recolorable	= TRUE
		overlay_file	= "/arrows/arrow-down.png"
		overlay_border	= { 2 ,2 , 2 ,2}
		overlay_stretch	= FALSE
		arrow_direction	= DOWN
	}


}

}

style "tabs"  = "default"
{
xthickness = 1
ythickness = 1

engine "pixmap"
{

	image
	{
		function	= EXTENSION
		state		= NORMAL
		gap_side	= BOTTOM
		file		= "/tabs/tab-top-active.png"
		stretch		= TRUE
		border		= { 2 ,2 ,2 ,2}
	}

	image
	{
		function	= EXTENSION
		state		= ACTIVE
		gap_side	= BOTTOM
		file		= "/tabs/tab-top.png"
		stretch		= TRUE
		border		= { 2 ,2 ,2 ,2}
	}


	image
	{
		function	= EXTENSION
		state		= NORMAL
		gap_side	= TOP
		file		= "/tabs/tab-bottom-active.png"
		stretch		= TRUE
		border		= { 2 ,2 ,2 ,2}
	}

	image
	{
		function	= EXTENSION
		state		= ACTIVE
		gap_side	= TOP
		file		= "/tabs/tab-bottom.png"
		stretch		= TRUE
		border		= { 2 ,2 ,2 ,2}
	}

	image
	{
		function	= EXTENSION
		state		= NORMAL
		gap_side	= LEFT
		file		= "/tabs/tab-right-active.png"
		stretch		= TRUE
		border		= { 2 ,2 ,2 ,2}
	}

	image
	{
		function	= EXTENSION
		state		= ACTIVE
		gap_side	= LEFT
		file		= "/tabs/tab-right.png"
		stretch		= TRUE
		border		= { 2 ,2 ,2 ,2}
	}

	image
	{
		function	= EXTENSION
		state		= NORMAL
		gap_side	= RIGHT
		file		= "/tabs/tab-left-active.png"
		stretch		= TRUE
		border		= { 2 ,2 ,2 ,2}
	}

	image
	{
		function	= EXTENSION
		state		= ACTIVE
		gap_side	= RIGHT
		file		= "/tabs/tab-left.png"
		stretch		= TRUE
		border		= { 2 ,2 ,2 ,2}
	}

	image
	{
		function	= BOX_GAP
		gap_side	= TOP
		file		= "/tabs/notebook_top_flat.png"
		stretch		= TRUE
		border		= { 1 ,1 ,1 ,1}
		gap_file	= "/tabs/tab-top-active-gap.png"
		gap_border	= { 1 ,1 ,1 ,1}
		gap_start_file	= "/tabs/null.png"
		gap_start_border= { 1 ,1 ,1 ,1}
		gap_end_file	= "/tabs/null.png"
		gap_end_border	= { 1 ,1 ,1 ,1}
		
	}

	image
	{
		function	= BOX_GAP
		gap_side	= BOTTOM
		file		= "/tabs/notebook_bottom_flat.png"
		stretch		= TRUE
		border		= { 1 ,1 ,1 ,1}
		gap_file	= "/tabs/tab-bottom-active-gap.png"
		gap_border	= { 1 ,1 ,1 ,1}
		gap_start_file	= "/tabs/null.png"
		gap_start_border= { 1 ,1 ,1 ,1}
		gap_end_file	= "/tabs/null.png"
		gap_end_border	= { 1 ,1 ,1 ,1}
		
	}

	image
	{
		function	= BOX_GAP
		gap_side	= LEFT
		file		= "/tabs/notebook_left_flat.png"
		stretch		= TRUE
		border		= { 1 ,1 ,1 ,1}
		gap_file	= "/tabs/tab-left-active-gap.png"
		gap_border	= { 1 ,1 ,1 ,1}
		gap_start_file	= "/tabs/null.png"
		gap_start_border= { 1 ,1 ,1 ,1}
		gap_end_file	= "/tabs/null.png"
		gap_end_border	= { 1 ,1 ,1 ,1}
		
	}

	image
	{
		function	= BOX_GAP
		gap_side	= RIGHT
		file		= "/tabs/notebook_right_flat.png"
		stretch		= TRUE
		border		= { 1 ,1 ,1 ,1}
		gap_file	= "/tabs/tab-right-active-gap.png"
		gap_border	= { 1 ,1 ,1 ,1}
		gap_start_file	= "/tabs/null.png"
		gap_start_border= { 1 ,1 ,1 ,1}
		gap_end_file	= "/tabs/null.png"
		gap_end_border	= { 1 ,1 ,1 ,1}
		
	}

	

}
}

style "combobutton" = "default"
{



engine "pixmap"
{



	image
	{
		function	= BOX
		state		= NORMAL
		file		= "/entry/entry-button-normal.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= PRELIGHT
		shadow		= OUT
		file		= "/entry/entry-button-prelight.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		state		= PRELIGHT
		shadow		= IN
		file		= "/entry/entry-button-prelight.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		state		= INSENSITIVE
		file		= "/entry/entry-button-normal.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}


	image
	{
		function	= BOX
		state		= ACTIVE
		file		= "/entry/entry-button-prelight.png"
		border		= { 4 ,4 , 4 ,4}
		stretch		= TRUE
	}


}

}

style "comboentry" = "default"
{

xthickness = 2
ythickness = 2

GtkWidget::interior_focus = 1

engine "pixmap"
{

	image
	{
		function	= FOCUS
		recolorable	= TRUE
		file		= "/entry/combo-active.png"
		border		= { 2 , 2 , 2 ,2 }
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		shadow		= OUT
		state		= NORMAL
		detail		= "entry"
		file		= "/entry/combo-inactive.png"
		border		= { 2 , 2 , 2 ,2 }
		stretch		= TRUE
	}

	image
	{
		function	= SHADOW
		state		= NORMAL
		recolorable	= FALSE
		shadow		= IN
		detail		= "entry"
		file		= "/entry/combo-inactive.png"
		border		= { 2 , 2 , 2 ,2 }
		stretch		= TRUE
	}



}

}


style "entry" = "default"
{

xthickness = 2
ythickness = 2

GtkWidget::interior_focus = 1

engine "pixmap"
{

	image
	{
		function	= FOCUS
		recolorable	= TRUE
		file		= "/entry/entry-active.png"
		border		= { 2 , 2 , 2 ,2 }
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		recolorable	= TRUE
		shadow		= OUT
		state		= NORMAL
		detail		= "entry"
		file		= "/entry/entry-inactive.png"
		border		= { 2 , 2 , 2 ,2 }
		stretch		= TRUE
	}

	image
	{
		function	= SHADOW
		state		= NORMAL
		recolorable	= FALSE
		shadow		= IN
		detail		= "entry"
		file		= "/entry/entry-inactive.png"
		border		= { 2 , 2 , 2 ,2 }
		stretch		= TRUE
	}


	image
	{
		function	= ARROW
	}

	image
	{
		function	= BOX
		state		= NORMAL
		detail		= "spinbutton_up"
		recolorable	= TRUE
		file		= "/scrollbar/spin-up.png"
		border		= { 3 , 3 , 3 , 3 }
		stretch		= TRUE
		overlay_file	= "/scrollbar/arrow-up.png"
		overlay_stretch	= FALSE
		overlay_border	= { 0 , 0 , 0 , 0 }
	}

	image
	{
		function	= BOX
		state		= PRELIGHT
		detail		= "spinbutton_up"
		recolorable	= TRUE
		file		= "/scrollbar/spin-up.png"
		border		= { 3 , 3 , 3 , 3 }
		stretch		= TRUE
		overlay_file	= "/scrollbar/arrow-up-prelight.png"
		overlay_stretch	= FALSE
		overlay_border	= { 0 , 0 , 0 , 0 }
	}

	image
	{
		function	= BOX
		state		= ACTIVE
		detail		= "spinbutton_up"
		recolorable	= TRUE
		file		= "/scrollbar/spin-up.png"
		border		= { 3 , 3 , 3 , 3 }
		stretch		= TRUE
		overlay_file	= "/scrollbar/arrow-up-prelight.png"
		overlay_stretch	= FALSE
		overlay_border	= { 0 , 0 , 0 , 0 }
	}

	image
	{
		function	= BOX
		state		= INSENSITIVE
		detail		= "spinbutton_up"
		recolorable	= TRUE
		file		= "/scrollbar/spin-up.png"
		border		= { 3 , 3 , 3 , 3 }
		stretch		= TRUE
		overlay_file	= "/scrollbar/arrow-up-insensitive.png"
		overlay_stretch	= FALSE
		overlay_border	= { 0 , 0 , 0 , 0 }
	}



	image
	{
		function	= BOX
		state		= NORMAL
		detail		= "spinbutton_down"
		recolorable	= TRUE
		file		= "/scrollbar/spin-down.png"
		border		= { 0 , 0 , 0 , 0 }
		stretch		= TRUE
		overlay_file	= "/scrollbar/arrow-down.png"
		overlay_stretch	= FALSE
		overlay_border	= { 0 , 0 , 0 , 0 }
	}

	image
	{
		function	= BOX
		state		= PRELIGHT
		detail		= "spinbutton_down"
		recolorable	= TRUE
		file		= "/scrollbar/spin-down.png"
		border		= { 0 , 0 , 0 , 0 }
		stretch		= TRUE
		overlay_file	= "/scrollbar/arrow-down-prelight.png"
		overlay_stretch	= FALSE
		overlay_border	= { 0 , 0 , 0 , 0 }
	}

	image
	{
		function	= BOX
		state		= ACTIVE
		detail		= "spinbutton_down"
		recolorable	= TRUE
		file		= "/scrollbar/spin-down.png"
		border		= { 0 , 0 , 0 , 0 }
		stretch		= TRUE
		overlay_file	= "/scrollbar/arrow-down-prelight.png"
		overlay_stretch	= FALSE
		overlay_border	= { 0 , 0 , 0 , 0 }
	}

	image
	{
		function	= BOX
		state		= INSENSITIVE
		detail		= "spinbutton_down"
		recolorable	= TRUE
		file		= "/scrollbar/spin-down.png"
		border		= { 0 , 0 , 0 , 0 }
		stretch		= TRUE
		overlay_file	= "/scrollbar/arrow-down-insensitive.png"
		overlay_stretch	= FALSE
		overlay_border	= { 0 , 0 , 0 , 0 }
	}


}

}


style "toolbar"
{
xthickness = 1
ythickness = 0
engine "pixmap"
{
	image
	{
		function	= BOX
		file		= "/toolbar/toolbar.png"
		border		= { 2 , 2 , 2 , 2 }
		stretch		= TRUE
	}
}
}

style "range" #= "default"
{
engine "pixmap"
{

	image
	{

		function	= BOX
		#recolorable	= TRUE
		#detail		= "trough"
		file		= "/range/trough-horiz.png"
		border		= { 9 , 9 ,2 ,2}
		stretch		= TRUE
		orientation	= HORIZONTAL
	}



	image
	{

		function	= BOX
		#recolorable	= TRUE  #when I comment these two lines it seems to fix the 
		#detail		= "trough" #problem with these pixmaps not being loaded
		file		= "/range/trough-vert.png"
		border		= {2 ,2 ,9 ,9}
		stretch		= TRUE
		orientation	= VERTICAL
	}

	image
	{

		function	= SLIDER
		recolorable	= TRUE
		state		= NORMAL
		file		= "/range/null.png"
		border		= { 0 , 0 ,0 ,0}
		stretch		= TRUE
		overlay_file	= "/range/slider-horiz.png"
		overlay_stretch	= FALSE
		orientation	= HORIZONTAL
	}

	image
	{

		function	= SLIDER
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/range/null.png"
		border		= { 0 , 0 ,0 ,0}
		stretch		= TRUE
		overlay_file	= "/range/slider-horiz-prelight.png"
		overlay_stretch	= FALSE
		orientation	= HORIZONTAL
	}

	image
	{

		function	= SLIDER
		recolorable	= TRUE
		state		= INSENSITIVE
		file		= "/range/null.png"
		border		= { 0 , 0 ,0 ,0}
		stretch		= TRUE
		overlay_file	= "/range/slider-horiz.png"
		overlay_stretch	= FALSE
		orientation	= HORIZONTAL
	}

	image
	{

		function	= SLIDER
		recolorable	= TRUE
		state		= NORMAL
		file		= "/range/null.png"
		border		= { 0 , 0 ,0 ,0}
		stretch		= TRUE
		overlay_file	= "/range/slider-vert.png"
		overlay_stretch	= FALSE
		orientation	= VERTICAL
	}

	image
	{

		function	= SLIDER
		recolorable	= TRUE
		state		= PRELIGHT
		file		= "/range/null.png"
		border		= { 0 , 0 ,0 ,0}
		stretch		= TRUE
		overlay_file	= "/range/slider-vert-prelight.png"
		overlay_stretch	= FALSE
		orientation	= VERTICAL
	}

	image
	{

		function	= SLIDER
		recolorable	= TRUE
		state		= INSENSITIVE
		file		= "/range/null.png"
		border		= { 0 , 0 ,0 ,0}
		stretch		= TRUE
		overlay_file	= "/range/slider-vert.png"
		overlay_stretch	= FALSE
		orientation	= VERTICAL
	}

}

}

style "statusbar" = "default"
{
engine "pixmap"
{

	image
	{
		function	= RESIZE_GRIP
		recolorable	= TRUE
		detail		= "statusbar"
		overlay_file	= "/other/statusgrip.png"
		overlay_border	= { 0 , 0 , 0 , 0}
		overlay_stretch	= TRUE
	}
}

}

style "progressbar" = "default"
{
xthickness = 2
ythickness = 2

bg[PRELIGHT] = "#000000"
fg[PRELIGHT] = "#5E78FC"



engine "pixmap"
{

	image
	{

		function	= BOX
		recolorable	= TRUE
		detail		= "trough"
		file		= "/progressbar/trough-progressbar-horiz.png"
		border		= { 6 , 6 , 4 ,4}
		stretch		= TRUE
		orientation	= HORIZONTAL
	}



	image
	{

		function	= BOX
		recolorable	= TRUE
		detail		= "bar"
		file		= "/progressbar/progressbar-horiz.png"
		border		= { 2 , 2 , 2 , 2}
		stretch		= TRUE
		orientation	= HORIZONTAL
	}

	image
	{

		function	= BOX
		recolorable	= TRUE
		detail		= "trough"
		file		= "/progressbar/trough-progressbar-vert.png"
		border		= {4 , 4 ,6 , 6}
		stretch		= TRUE
		orientation	= VERTICAL
	}

	image
	{

		function	= BOX
		recolorable	= TRUE
		detail		= "bar"
		file		= "/progressbar/progressbar-vert.png"
		border		= { 2 , 2 , 2 ,2}
		stretch		= TRUE
		orientation	= VERTICAL
	}
}
}

style "layout"
{
engine "pixmap"
{
	image
	{
		function	= SHADOW
		detail		= "entry"
		recolorable	= FALSE
		shadow		= IN
		file		= "entry/entry-inactive.png"
		border		= {4 , 4 ,4 ,4 }
		stretch		= TRUE
	}

	image
	{
		function	= BOX
		detail		= "button"
		recolorable	= FALSE
		state		= NORMAL
		file		= "button/button-normal.png"
		border		= {4 , 4 ,4 ,4 }
		stretch		= TRUE
	}

}
}

style "nostyle" = "default"
{
engine "pixmap"
{
	image
	{
		function	= SHADOW
	}
}
}

style "unstyle"
{
engine "pixmap"
{}
}

style "cruxtext"
{
engine "crux-engine" {

}


}


# widget styles
class "GtkWidget"      				style "default"
class "GtkButton"      				style "button"
class "GtkCombo*"       			style "optionmenu"
widget_class "*GtkCombo*"       		style "optionmenu"
class "GtkOptionMenu"       			style "optionmenu"
class "GtkRange"       				style "range"
class "GtkFrame"       				style "default"
class "GtkMenu"        				style "menu"
widget_class"*Menu*"        			style "menu"
widget_class"*MenuItem*"        		style "menuitem"
widget_class"*MenuItem.*"        		style "menuitem"
widget_class"*.GtkMenuItem.*"        		style "menuitem"
widget_class"*.GtkAccelMenuItem.*"        	style "menuitem"


class "GtkMenuItem"    				style "menuitem"
class "GtkImageMenuItem"    			style "menuitem"
class "GtkTearoffMenuItem"    			style "menuitem"
class "GtkItem"    				style "menuitem"
#class "GtkEntry"       				style "entry"
#class "GtkOldEditable"				style "entry"
class "GtkNotebook"    				style "tabs"
class "GtkProgressBar" 				style "progressbar"
widget_class "*ProgressBar*" 			style "progressbar"
widget_class "*MenuItem.*ProgressBar*" 		style "progressbar"

#class "MetaFrames"     				style "metacity-frame"
#class "GtkWindow"      				style "metacity-frame"
class "GtkScrollbar"				style "scrollbars"
class "GtkStatusbar"				style "statusbar"
class "*MenuBar*"				style "menubar"
widget_class "*MenuBar.*"			style "menubar"

class "*Font*"					style "optionmenu"


widget_class "*Entry*Button*"       		style "combobutton"
class "GtkEntry"       				style "entry"
class "GtkOldEditable"				style "entry"
widget_class "*GtkCombo.*Button*" 		style "combobutton"
widget_class "*Combo*Entry*"    		style "comboentry"


class "GtkHandleBox"				style "default"
class "GtkPaned"				style "default"
class "GtkSpinButton" 				style "entry"
class "GtkCheckButton" 				style "checkbutton"
class "GtkCheckMenuItem" 			style "checkbutton-menu"
class "GtkRadioButton" 				style "radiobutton"
class "GtkCheckMenuItem" 			style "radiobutton-menu"
widget "gtk-tooltips" 				style "default"

class "PanelDItemEditor"			style "default"

class "GtkEventBox"				style "nostyle"
class "SPColorSlider"				style "unstyle"
# treeview stuff

widget_class "*.GtkCTree.GtkButton" 		style "listheader"
widget_class "*.GtkList.GtkButton" 		style "listheader"
widget_class "*.GtkCList.GtkButton" 		style "listheader"
class "GtkLayout"				style "layout"



class "GtkToolBar"				style "nostyle"
widget_class "*.GtkTool*"			style "toolbar"
widget_class "*Tool*Button*"      		style "toolbutton"
widget_class "*Tool*GtkToggleButton"  		style "toolbutton"
widget_class "*SpinButton*" 			style "entry"

#the following is my desperate try to use the crux engine to draw (disabled) text
#to get rid of that annoying shadow, if you have more fixes or better ones, please 
#let me know

class "*Label*"					style "cruxtext"
widget_class "*Label*"				style "cruxtext"
widget_class "*Cell*"				style "cruxtext"
widget_class "*.GtkTreeView"			style "cruxtext"
widget_class "*.GtkTreeView.GtkButton" 		style "listheader"

# combobox stuff
#widget_class "*.GtkComboBox*" 			style "entry"
#widget_class "*.GtkCombo*Entry*"    		style "entrytext"


# tooltips stuff
#widget_class "*.tooltips.*.GtkToggleButton" 	style "clearlooks-tasklist"



#widget_class "*.GtkFrame.GtkLabel" 		style "clearlooks-frame-title"

# notebook stuff
#widget_class "*.GtkNotebook.*.GtkEventBox" 	style "aura"
#widget_class "*.GtkNotebook.*.GtkViewport" 	style "aura"

# these should really use base and text colors instead
#widget_class "*GtkCTree*" style "evolution-hack"
#widget_class "*GtkList*" style "evolution-hack"
#widget_class "*GtkCList*" style "evolution-hack"
#widget_class "*.ETree.*" style "evolution-hack"

widget "*.nautilus-extra-view-widget" style:highest "default" #this seems to fix a blue line above scroll
#bars in nautilus
```


Thank you in advance!

---

### Post by marlin9800 on 2009-08-25
I don't see any attachments, but I believe I am having a very similar problem.

I have applied a theme to my desktop (Darker Theme) which changes the main panel's background to an image. It looks nice but I like my top panel to be 32 pixels, not the default 24. No big deal, I change the panel background to 'Solid color' with some transparency and I am happy; almost. The item 'Window Selector' (most of them for that matter, like Notification Area and Volume control) keeps the theme's background image and just looks bad. Not trying to hijack the OP, I just think we are asking the same thing.

Edit: added screenshot

---

### Post by Zopiac on 2009-08-25
> **marlin9800 said:**
> I don't see any attachments, but I believe I am having a very similar problem.

Well thats weird...lets try again

Edit: There we go :)

---

### Post by Stevie78 on 2009-08-25
Have you installed Emerald?

You can change the transparency level of the panels by right-clicking them and then editing the properties.

---

### Post by Zopiac on 2009-08-25
> **Stevie78 said:**
> Have you installed Emerald?


Yes, I have.

> **Stevie78 said:**
> You can change the transparency level of the panels by right-clicking them and then editing the properties.

Is this dealing with Emerald? If not, I have already said that this does not work.

---

### Post by bodhi.zazen on 2009-08-25
It looks partially transparent. Right click on the panel and select properties. you can change the transparency up or down if you wish.

I think the problem is that the contents of the panel, ie the icons, they are not transparent.

---

### Post by marlin9800 on 2009-08-25
Ok, my problem was the theme, just different themes act differently. (Ref: [http://ubuntuforums.org/showthread.php?t=205087](http://ubuntuforums.org/showthread.php?t=205087))

So I changed to a new theme that had a backgroud image that resixed based on the panel size, SlicknesS (an old theme I had for a while and just rediscovered).

---

### Post by Zopiac on 2009-08-25
> **bodhi.zazen said:**
> I think the problem is that the contents of the panel, ie the icons, they are not transparent.

Well the background of the icons is the theme graphic for the panel. If the theme graphic (not the background selected in the Properties) was transparent, I believe that this would work.

---

### Post by Zopiac on 2009-08-28
Bump?

---

