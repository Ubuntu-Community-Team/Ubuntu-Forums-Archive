---
title: "Editing userchrome.css for firefox"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by browny254 on 2010-03-26
Hi,

When I installed firefox lots of the menus and toolbars displayed in a really large font, I think it has something to do with the fontsdpi settings as if I change that to force 96dpi it displays firefox correctly, but then everything else (ie plasma icons, panels and the like) displays really small.

So I have been editing userChrome.css for firefox and have managed to get the main toolbars, status bar and address/search boxes to display how I like, but there are still a lot of things that dont display correctly. I have attached a few screenshots showing this, they include things such as any dialog popups such as the preferences screen, or any addons preferences screen for that matter, also the search bar and also I noticed as I was about to post this, the boxes on this forum for selecting prefix/title for the new thread and submit/preview buttons are also very large.

Can anyone help me get this fixed please.

Thanks.

---

### Post by mzalfres on 2010-03-26
I'd start with cleaning up your firefox config completely. Just for trial - close ff, rename your $HOME/.mozilla dir to something like $HOME/.mozilla_old and run ff again. Then look what is wrong and eventually give some pictures. At this point I have no idea what is effect of your modifications and what is a system related problem.

---

### Post by browny254 on 2010-03-26
This is a brand new install of firefox, infact I only installed kubuntu a few hours ago. I have had this problem for months on my regular computer but it has died and so im now using a netbook as my primary computer so before it was just an annoyance, now its a porblem.

this is my userChrome.css now. I dont really know css and everything in it is from stuff I have googled and then trialed until I worked out what it did.

```
/*Do not remove the @namespace line -- it's required for correct functioning*/
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");


/*Toolbar & menu font size*/
menubar, menubutton, menulist, menu, menuitem, textbox, toolbar, tab, tree, tooltip{font-size: 6pt !important;}

/*Toobar height*/
toolbar {max-height:28px !important;}
#toolbar-menubar {padding: 0px !important;}

/* Remove menus and sizing */
#helpMenu,  #history-menu, #view-menu, #bookmarksMenu {display: none !important;}
#file-menu, #edit-menu, #tools-menu {padding: 1px !important}


/*Status bar height and font size*/
#status-bar {padding: 0px !important; max-height: 15px !important; font-size: 6pt !important;}


/*auto-complete list size and font*/
.autocomplete-richlistitem {font-size: 6pt !important; padding: 0px !important; margin: 0px !important;}


/* Remove Stop button when there's nothing to Stop */
#stop-button[disabled="true"] { display: none; }

/* Remove Home button */
#home-button { display: none; }

/*Remove forward/back list arrow when nothing to go to*/
#back-forward-dropmarker[disabled="true"] {display: none;}

/*Button padding*/
#back-button, #forward-button, #reload-button, #stop-button, #back-forward-dropmarker {padding: 0px !important}

```

I have attached a screenshot if I remove this, showing the default state.

---

