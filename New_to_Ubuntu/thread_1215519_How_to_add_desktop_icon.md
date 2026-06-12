---
title: "How to add desktop icon?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by oxf on 2009-07-17
OK silly basic questions here. I just installed Acroread. However, when I create a link to it on the desktop all I get  is a generic folder type image and not the proper logo icon. So how do I add the logo Icon so it looks decent?

Also on launch I'm getting a message that its not a trusted application. How do I add it add it as a "trusted application"?

Thanks

---

### Post by NilsE on 2009-07-17
As far as the icon goes, you can go into properties for the launcher and click on the icon on the top left and pick your own. If you choose something from one of the menus and right click and say create launcher I believe it will make it with the correct icon.

I have never seen the trusted app message so I am not sure where to point you on that one.

---

### Post by oxf on 2009-07-17
> **NilsE said:**
> As far as the icon goes, you can go into properties for the launcher and click on the icon on the top left and pick your own. If you choose something from one of the menus and right click and say create launcher I believe it will make it with the correct icon.

I have never seen the trusted app message so I am not sure where to point you on that one.

Yes I tried that. The problem is that the icon within launcher properties is just a the "blank page with folded corner" symbol and when I click on it takes me to the places/files. I suspect it has something to do with the fact that the "generic file" icon on the desktop has the locked symbol on it? 

I was a tad suprised I didnt get a "proper" icon when I installed it TBH. I went to software  sources added to the repositories and then used sudo apt-get acroread to install. While it apears to work ok (except the trusted app msg) the lack of icon looks a bit grotty!
Thanks

---

### Post by drs305 on 2009-07-17
When you attempt to update the icon location, try putting this in as the address:
> /usr/local/share/icons/hicolor/48x48/apps/AdobeReader9.png

If you don't have Reader9, your version's icon should be in the general area.

---

### Post by oxf on 2009-07-17
> **drs305 said:**
> When you attempt to update the icon location, try putting this in as the address:


If you don't have Reader9, your version's icon should be in the general area.

Yes I have Reader 9. The thing is this. I add that address, or go down the file tree, and when I get to that icon "add" on the left is greyed out. So I click on "open" and it closes the window and I'm back at properties again at square one!

---

### Post by drs305 on 2009-07-17
If it's merely an icon problem and not something more complicated: 
I navigate/paste */usr/local/share/icons/hicolor/48x48/apps/* and select "Open" in the lower right. Sometimes the icons display, but other times I have to hit the lower right "cancel" and then the icons appear.

Here may be another way around it. Substitute where you want the icon to permanently reside for the Desktop location in the example:
```

sudo cp /usr/local/share/icons/hicolor/48x48/apps/AdobeReader9.png $HOME/Desktop/
sudo chown *yourusername* $HOME/Desktop/AdobeReader9.png

```
Then use the icon in the new location as your icon.

---

### Post by oxf on 2009-07-17
> **drs305 said:**
> If it's merely an icon problem and not something more complicated: 
I navigate/paste */usr/local/share/icons/hicolor/48x48/apps/* and select "Open" in the lower right. Sometimes the icons display, but other times I have to hit the lower right "cancel" and then the icons appear.

Here may be another way around it. Substitute where you want the icon to permanently reside for the Desktop location in the example:
```

sudo cp /usr/local/share/icons/hicolor/48x48/apps/AdobeReader9.png $HOME/Desktop/
sudo chown *yourusername* $HOME/Desktop/AdobeReader9.png

```Then use the icon in the new location as your icon.

OK I've almost sorted it! Before trying your sugestion I noticed that the permissions were different for this icon than my other desktop icons, i.e the owner was root as opposed to me. I went to terminal and used gksu nautilaus and changed the permissions to my username and also checked "allow executing file as progam" That alowed me to change the icon (and also takes care of the "trusted user" issue).

The only thing is the Icon has a arrow pointing out of the upper right corner? this is the only one of my desktop icons that does. Can I get rid of that?

---

