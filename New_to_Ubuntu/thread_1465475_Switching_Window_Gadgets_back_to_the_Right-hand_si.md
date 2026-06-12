---
title: "Switching Window Gadgets back to the Right-hand side on 10.04"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2010-04-29
If new users are wondering how to switch the window gadgets back to the right hand side here is how its done.

There is many webpages emerging on how to put them back this is one:[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/")

PS: If you run "gconf-editor" from the terminal, and know where to look (weblink above) you can change the button layout to anything you want by changing the order (No BS it's true). LOL

PPS: The new version of "ubuntu tweak" allows this too, which should be available soon :-)

---

### Post by Calash on 2010-04-29
Are they really called gadgets?  I always call them window controls.

Good post, hopefully it will help answer some of the questions.

---

### Post by Nightstrike2009 on 2010-04-29
Cheers Calash,

Its up to you what you wish to call them my friend.

It was mentioned it would confuse newcomers having them on the left, while i was using a beta version. I promised that has soon as Ubuntu 10.04 final was released, I would share the info with newcomers, glad to help.

*The instructions are based on a beta version but should still work in the final version.*

> **From [http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/")**

**_How to move the window buttons_**

The window button locations are dictated by a configuration file. We&#8217;ll use the graphical program gconf-editor to change this configuration file.

Press Alt+F2 to bring up the Run Application dialog box, enter &#8220;gconf-editor&#8221; in the text field, 
and click on Run.

The Configuration Editor should pop up.
The key that we want to edit is in apps/metacity/general.

Click on the + button next to the &#8220;apps&#8221; folder, then beside &#8220;metacity&#8221; in the list of folders expanded for apps, and then click on the &#8220;general&#8221; folder.

The button layout can be changed by changing the &#8220;button_layout&#8221; key. Double-click button_layout to edit it.

Change the text in the Value text field to:
:close,minimize,maximise

*(Delete the menu part, this differs from website instructions but works correctly now)*

Click OK and the change will occur immediately, changing the location of the window buttons in the Configuration Editor.

Note that this ordering of the window buttons is slightly different than the typical order; in previous versions of Ubuntu and in Windows, the minimize button is to the left of the maximize button.

You can change the button_layout string to reflect that ordering, but using the default Ubuntu 10.04 theme, it looks a bit strange.

If you plan to change the theme, or even just the graphics used for the window buttons, then this ordering may be more natural to you.

**_After_**

After this change, all of your windows will have the maximize, minimize, and close buttons on the right.



PS: The reason for the detailed quote was the original website I linked to in beta testing went down. I had to find a replacement one (the one above) with it in quote it should save newcomers trouble, while rightfully crediting the source and maintaining the info. :-)

---

### Post by Mr. Picklesworth on 2010-04-29
That really isn't the best way to do this. Each theme now has its own preferred placement for window buttons, so editing the gconf key manually is more complicated than it needs to be and could damage a potentially awesome little feature.

The easiest solution: just choose a different theme. Homosapien is a beautiful theme available right away.
(Oops. As Nightstrike points out, the theme I mentioned isn't available quite immediately. You need to [install the community-themes package]("apt:community-themes") and then it will be available).

More info in this thread: [http://ubuntuforums.org/showthread.php?t=1463878](http://ubuntuforums.org/showthread.php?t=1463878)
Ambience / Radiance themes with buttons on the right: [http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz](http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz)

---

### Post by kingofpain on 2010-04-29
Thanks a lot! :mrgreen:

---

### Post by J V on 2010-04-29
Is it just me or did they change the order of the buttons? Not the position, the order...

I downloaded a daily build and my buttons are close,minimize,maximize:menu...

---

### Post by Nightstrike2009 on 2010-04-29
The pre-installed theme "New Wave" also has the gadgets on the right hand side.

In answer to J V, I am now running Ubuntu 10.04 LTS (Final) my gconf-editor key reads:

close,minimize,maximize:     

Before I changed it to:

:close,minimize,maximize

I think they did alter the sequence during beta testing but not sure at what stage.

PS: **To Mr. Picklesworth**: The "Homosapien" theme isn't installed by default on Ubuntu 10.04LTS 
(At least not on mine anyhow)

I would also like to point out that Ubuntu is open-source and free to be modified by its users at will, many of the users didn't ask for the window gadgets to change position and are free to rectify this as they wish.

I acknowledge that gconf-editor must be used with caution (hence providing detailed instructions) and I have also discovered the new version of "ubuntu-tweak" also has an option for switching them from one side to the other for the more cautious users should be available here [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

---

### Post by alvevind on 2010-04-29
The cleanest way to move the windows back to standard is to install the right aligned theme (mentioned by Mr.Pricklesworth).

Step-by-step procedure:
1. Download the modified theme [http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz](http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz)
2. Open the menu "System" > "Preferences" > "Appearance"
3. Click the button "Install"
4. Open the folder "Downloads"
5. Select the file "Ambience_Radiance-Right.tar.gz"
6. Click "Open"
7. Select the new theme "Ambiance-right"

---

### Post by Nightstrike2009 on 2010-04-29
Until you delete the right hand themes and it won't let you reinstall.

The easiest way is install "Ubuntu Tweak" vers 0.5.3

Under "Desktop"
Select "Window Manager Settings"
under "Window Titlebar Button Layout"
chose "Left" or "Right"

Thats it :-)

PS: Id rather install "ubuntu tweak" or learn a bit about "gconf-editor" than fill my system up with duplicated files/themes I don't want or require, but thats just my opinion. :-)

---

### Post by Teber on 2010-04-29
i changed the window theme to human-clearlooks. and everything looks perfectly clear again to me...

it's all under system/preferences/appearance

---

### Post by Mr. Picklesworth on 2010-04-29
> **Nightstrike2009 said:**
> PS: Id rather install "ubuntu tweak" or learn a bit about "gconf-editor" than fill my system up with duplicated files/themes I don't want or require, but thats just my opinion. :-)

Oh, no, they aren't duplicating anything. They reference the original Ambiance and Radiance themes as they are, simply stating a new button_layout key. The size of the two themes combined is measured in bytes.

The reason I am keen on this approach is because having window button layout attached to themes is a very new change that very few people know about, and it will be very useful for everyone to follow that approach.

For a quick demonstration of one reason why, change your theme to something else, then change it back to Ambiance.
There goes your customization, and there enters a confused user.

---

### Post by alvevind on 2010-04-29
> **Mr. Picklesworth said:**
> For a quick demonstration of one reason why, change your theme to something else, then change it back to Ambiance.
There goes your customization, and there enters a confused user.

Very good point!

---

### Post by moe46 on 2010-04-30
This left handed button thing really had me pissed of but if its not innate and its just a theme then its not so bad. That being said they should have left the buttons the way they were and just added the left hand theme, or at minimum included the right handed theme in the release.

---

### Post by Rakali on 2010-05-03
> **moe46 said:**
> This left handed button thing really had me pissed of but if its not innate and its just a theme then its not so bad. That being said they should have left the buttons the way they were and just added the left hand theme, or at minimum included the right handed theme in the release.

It was a little confusing that the buttons swapped over to the other side for no apparent reason. Is this a normal setting for Linux GUIs?

So glad I found this forum!

---

### Post by germanix on 2010-05-03
I do appreciate und understand that some people are unhappy with the window buttons having been moved to the left side of the window. A lot of people especially those coming from MS Windows are used to having them on the right side however users like myself who comes from and still use Apple OSX on a daily basis find this change very good as we have learned to appreciate having these buttons on the left. When I originally changed from Windows to OSX having those buttons on the left did confuse me for a couple of days but I quickly became accustomed to the change and after a while I realised that having the buttons on the left was far more natural to use than otherwise. We also read starting from the left and not from the right side of a page. I can only advise that one should give it a try, perhaps you too will see the benefit of it after a short while. I for one am very happy that these buttons are now on the left. I would nor have it any other way.

---

### Post by Georgia boy on 2010-05-03
All I did was right click on the desktop and went to change background. Didn't mess with anything else. Clicked on Change Themes and tried the different ones available. But, for some reason I kind of like the selections on the left side. After playing with the themes having them on the right I changed back to them being on the left side again. Might change back later, don't know for sure but for now it's one of those new things to play with. 

Tom

---

### Post by 3rdalbum on 2010-05-03
We should all get used to having the buttons on the left, because there's some quite innovative and exciting things coming to the right-hand side of the titlebar. Check out [www.markshuttleworth.com](www.markshuttleworth.com) for more details.

---

### Post by lalaland on 2010-05-06
"We should all get used to having the buttons on the left, because there's some quite innovative and exciting things coming to the right-hand side of the titlebar. "
Why can't the exciting new stuff go on the left?

---

### Post by Nightstrike2009 on 2010-05-06
Lets face it this will probably run for a long-time with neither side reaching an agreement. Some prefer the left others right, if 3rdalbum is correct > **By 3rdalbum:** We should all get used to having the buttons on the left, because there's some quite innovative and exciting things coming to the right-hand side of the titlebar. Check out [www.markshuttleworth.com]("www.markshuttleworth.com")  for more details.

Then at least there is a point made that I was unaware of before, and Mr Picklesworth seems more knowledgable than I originally expected so I apologise to you about any pre-conceptions I had some just argue for the sake of it but you make your point well and though I will continue to use gconf-editor I respect your opinion and understand what you mean now. :-)

I also get this point > **By lalaland:**"We should all get used to having the buttons on the left, because there's some quite innovative and exciting things coming to the right-hand side of the titlebar. "
Why can't the exciting new stuff go on the left?

I second that lalaland, it would have been far less confusing for us all. :-)

---

### Post by Calash on 2010-05-06
> **lalaland said:**
> "We should all get used to having the buttons on the left, because there's some quite innovative and exciting things coming to the right-hand side of the titlebar. "
Why can't the exciting new stuff go on the left?

It is trying to remain constant with notifications being at the top right.  IMHO we will have the option to move it anywhere we want, probably in the same key as we can alter the button locations now.

Don't quote me on that as nothing is really known about the new notifications yet, just my gut feeling.

---

### Post by mastablasta on 2010-05-06
> **germanix said:**
> I do appreciate und understand that some people are unhappy with the window buttons having been moved to the left side of the window. 
 
yah depends really i guess on previous experience. I keep thinking if having a bar on top is better or not. i am so used to just blindly move mouse to top right corner and clicking if i want to close something. i don't even have to look in win as that move always closes the window.

---

### Post by mac25 on 2010-05-06
Simple and to the point help, thank you.I did not like the move or see any need for it.
The new update could not even sort out my monitor size.
So far not to impressed.

---

### Post by Krytarik on 2010-11-14
I found a python script a while ago, which provides a GUI to change the  configuration of the window controls. I modified it little so that it  indicates the current state of the controls and to also provide the  option to re-integrate the lost menu-button (might be helpfull  sometimes).

I have attached the respective files to install it in the usual way. I hope you enjoy it!

---

### Post by de_island on 2011-04-24
d

---

