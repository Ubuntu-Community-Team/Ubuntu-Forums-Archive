---
title: "start firefox addons (downthemall) via terminal"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by marshall31415 on 2009-09-02
hi.

i am looking for a way to start firefox and an addon via terminal.

"firefox" starts firefox. thats easy.

How can i get an addon to run automatically (specifically downthemall)? or is that just asking too much?

---

### Post by starcraft.man on 2009-09-02
I'm a bit confused. You just want to launch both immediately, or actually download from the terminal. If the latter, see the wget command, for more info in a terminal:
```
man wget
```

I don't really understand why ya'd do the former, you actually have to browse to page you want to download from before opening up the main downthemall window to select what you want to rip from the site highlighted. Opening it at launch, would simply have it set to rip from the home page or last session page which you've likely already seen no?

---

### Post by izziere on 2009-09-03
Well, Firefox loads the add-ons at startup.  Do you mean to bypass the menu selection required to display dta? My guess is that it can't be done. You seem to be asking whether you can use post-load commands from the terminal, which I can't see is possible.

---

### Post by marshall31415 on 2009-09-03
The addon "DownThemAll" for firefox has a GUI manager. The downloads automatically start when the GUI is opened. If firefox is opened, but the GUI for downthemall isnt - the downloads wont start.

I want to make a small program that :

1) checks if firefox is running.
2) if not starts firefox + DownThemAll
3) if it is kills the firefox process.

I want to bind this to a key, so I can have a "downloads on/off" toggle button.

Alternatively, is there a program that can batch download links from a webpage for Firefox in Ubuntu?

---

### Post by lovinglinux on 2009-09-03
> **marshall31415 said:**
> The addon "DownThemAll" for firefox has a GUI manager. The downloads automatically start when the GUI is opened. If firefox is opened, but the GUI for downthemall isnt - the downloads wont start.

I want to make a small program that :

1) checks if firefox is running.
2) if not starts firefox + DownThemAll
3) if it is kills the firefox process.

I want to bind this to a key, so I can have a "downloads on/off" toggle button.

Alternatively, is there a program that can batch download links from a webpage for Firefox in Ubuntu?

1) have no idea
2) to start the DwonThemAll manager you can use this:

```
firefox -chrome chrome://dta/content/dta/manager.xul
```

This is the way of opening extensions pages using the URI. Unfortunately, it doesn't seems to work this way, like other extensions. I don't know if it has some sort of protection or if was simply because I wasn't downloading anything. Anyway, you can also set your home page as **chrome://dta/content/dta/manager.xul**, so whenever you start Firefox from terminal, it will start your downloads.

3) you cannot kill firefox and keep DownThemAll running.

What I suggest is to create a another Firefox profile, just for DownThemAll. Run the code below to launch the profile manager, from where you can create a new profile. 

```
firefox -P
```

Save it as "Downloads" for example.

You can open it side-by-side with your regular profile with this:

```
firefox -P "Downloads" -no-remote
```

Then install DownThemAll on it, go to the Main tab in the Firefox Preferences and set the home page as **chrome://dta/content/dta/manager.xul**. Select the option "Show my home page" in the "When Firefox starts" option.

Then customize the interface to make it minimalistic, by hiding toolbars and icons for example. Then drag the download links from your regular Firefox profile window to the Downloads profile window. Close it. Start it again with:

```
firefox -P "Downloads" -no-remote
```

It should open DownThemAll and start your downloads.

The rest necessary to accomplish what you want is basically shell scripting. It shouldn't be hard to do it. Instead of killing firefox entirely, you can kill the process running each profile separately, since the -no-remote option launches a new firefox process.

---

### Post by marshall31415 on 2009-09-09
> **lovinglinux said:**
> 1) have no idea
2) to start the dwonthemall manager you can use this:

```
firefox -chrome chrome://dta/content/dta/manager.xul
```this is the way of opening extensions pages using the uri. Unfortunately, it doesn't seems to work this way, like other extensions. I don't know if it has some sort of protection or if was simply because i wasn't downloading anything. Anyway, you can also set your home page as **chrome://dta/content/dta/manager.xul**, so whenever you start firefox from terminal, it will start your downloads.

3) you cannot kill firefox and keep downthemall running.

What i suggest is to create a another firefox profile, just for downthemall. Run the code below to launch the profile manager, from where you can create a new profile. 

```
firefox -p
```save it as "downloads" for example.

You can open it side-by-side with your regular profile with this:

```
firefox -p "downloads" -no-remote
```then install downthemall on it, go to the main tab in the firefox preferences and set the home page as **chrome://dta/content/dta/manager.xul**. Select the option "show my home page" in the "when firefox starts" option.

Then customize the interface to make it minimalistic, by hiding toolbars and icons for example. Then drag the download links from your regular firefox profile window to the downloads profile window. Close it. Start it again with:

```
firefox -p "downloads" -no-remote
```it should open downthemall and start your downloads.

The rest necessary to accomplish what you want is basically shell scripting. It shouldn't be hard to do it. Instead of killing firefox entirely, you can kill the process running each profile separately, since the -no-remote option launches a new firefox process.


thank you so much

---

### Post by lovinglinux on 2009-09-09
> **marshall31415 said:**
> thank you so much

You are welcome. I'm glad it worked.

---

### Post by mufti on 2011-07-07
managed to start downthemall downloading with:
```
firefox -no-remote -chrome chrome://dta/content/dta/addurl.xul
```
but is there a way to pass url to it :confused:

---

### Post by uRock on 2011-07-07
This thread is very old. Please start a new thread.

Thread Closed.

---

