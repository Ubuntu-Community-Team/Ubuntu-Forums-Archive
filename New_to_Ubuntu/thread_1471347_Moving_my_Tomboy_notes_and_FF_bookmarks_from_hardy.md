---
title: "Moving my Tomboy notes and FF bookmarks from hardy to lucid?"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by hortstu on 2010-05-03
Looking for some help on this.  I have my drive set up like this...

```
all the partitions are under one extended partition sda1

sda5.....ext3.....hardy heron...............14.3GB
sda6.....ext3.....hardy home................2.86GB
sda7.....ext3.....lucid.....................14.3GB
sda8.....ext3.....lucid home?(not sure).....2.86GB
sda10....ext3.....shared data storage.......109GB
sda9.....ext3.....swap......................5.72GB
```

Now I've managed to access all my documents, spreadsheets etc from lucid but I can't figure out how to get a few other things into lucid from hardy without doing it manually.  I'm specifically stuck on tomboy notes and firefox bookmarks.

Can anyone tell me how to get these into lucid?

---

### Post by cariboo on 2010-05-03
Firefox bookmarks are located in ~/.mozilla/firefox/xxxxxxxx.default. where xxxxxxxx are a random string of letters and numbers. You cam import your bookmarks in Firefox by going to Bookmarks->Organize Bookmarks->Import and Backup->Import HTML then navigate to your home directory on your 8.04 installation, then to the above mentioned directory. ~/.mozilla is a hidden directory, so may have to use Ctrl-H to reveal the hidden files and directories.

---

### Post by hortstu on 2010-05-03
> **cariboo907 said:**
> Firefox bookmarks are located in ~/.mozilla/firefox/xxxxxxxx.default. where xxxxxxxx are a random string of letters and numbers. You cam import your bookmarks in Firefox by going to Bookmarks->Organize Bookmarks->Import and Backup->Import HTML then navigate to your home directory on your 8.04 installation, then to the above mentioned directory. ~/.mozilla is a hidden directory, so may have to use Ctrl-H to reveal the hidden files and directories.

Thanks cariboo I found what I believed was the file but it didn't contain a recent copy of my bookmarks.  I tried backing it up but that wasn't saved as an HTML file which seems to be what I'm looking for.  I did look for hidden folders but didn't see anything else.  

I'm looking for more help with importing my ff bookmarks and my tomboy notes.

Thanks

---

### Post by jimrz on 2010-05-03
1] for Tomboy go to ~/.tomboy on your Hardy install, where you can copy all of the .note files and paste them into your ~/.tomboy on Lucid and you will then have all your notes on each

2] for FF your bookmarks are contained in ~/.mozilla/firefox/bookmarks.html, just copy it from Hardy  and paste to Lucid, as above.


both .tomboy & .mozilla are hidden folders, so use ctl + h to show them in your file manager

---

### Post by hortstu on 2010-05-03
jim,

this is what's in my bookmarks.html file...

```
<!DOCTYPE NETSCAPE-Bookmark-file-1>
<!-- This is an automatically generated file.
     It will be read and overwritten.
     DO NOT EDIT! -->
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=UTF-8">
<TITLE>Bookmarks</TITLE>
<H1>Bookmarks</H1>

<DL><p>
    <DT><A HREF="https://en-US.add-ons.mozilla.com/en-US/firefox/bookmarks/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAFo9M%2F3AAAABGdBTUEAANbY1E9YMgAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAPkSURBVHjaYmAAgrjyOnOGiKxqxT9%2F%2FvwHCCCGuNJKLpAo49KTL%2F5%2F%2F8PMABBADJFZFWwXnn%2F%2FDxJYeOLNf0aQ9AIg48%2Ff%2Fwwfvv1hAAggZpBAYlWdnrqJLcPVE4e%2Bsuy7%2FfH%2F%2B88%2FGdjY2Bj%2BcCqHMey6%2Ben%2F379%2F%2F%2F8B6unZ9ew%2Fy54jV249f6%2Bm9uXnX4Y9qyaoAAQAhAB7%2FwEAAAAAY3h%2BG1RdbeMMCgkB9%2Fr%2BAPL2%2FAC3vsyi5NG6YQFcbnwdZ3F44uru9gAAAQAAUjEVALPT7wDu9v4A5erz%2FgL19vr16PD6AAUHBgDu9PwA%2F%2F8AAO%2F2%2FgD0%2BP0A7e7x8QPYzsX38vj9g%2BPk6hkLFiAxy%2BP4AeHj5%2FXFtp9GonxaagII7AawXyprpf%2F%2FZ5L5%2Fe%2Fv9%2B%2Fff91ZN7nrG0icJSqrkknJxHm1h5Nl0J8%2F%2Fxg%2B%2FwDa%2Febzv39%2FWKQ2TG97ycIvq%2Bvn52oVxMHGxHDj8RcGQT4uEGZyCct98e3LL3YmJ2enNYxAi%2B48%2B8QQaizGIMLFBLaSlYWZgYWDWZaJhY2V%2BcvPfwz%2BeiIMf%2F%2F%2BY9CV4GAQ42Zh%2BPPvP8O%2Fv%2F%2BZmG7cff7u49c%2FDNtufGZgYmJiOHLvG8Pt1z8Yfv3%2Bz%2FDn19%2B3TCd2LNV7%2F%2FU3w7vPvxkWnHzDcOPFd4ZvQBPv3L79aM%2BS3nfMN88d%2BfyXkW0Lq6BiGAs7J8fHT9%2F%2FXTy%2BY82Lp0cdb5889hcgQJNU85JYFMXP%2B5aHqRmmZJ9kKMGAEBgtDCYYY6BFa%2BlrPc6yRf0LYYtZzG4YaNGibUNJVLuIcBNUTLMQM8ZoppdiaXnf9Xlf5z4ounDu4p57f%2Ff8Pt50SH9ZEfUuLehy93yMRBNroVAg6PV2yBbO9c94tK5v7suF3%2FlMs1o8oU27ltvIMic7fJv7uuqLJGa2UpPxlCILICBtGz1pYWooakeoDaTFgBtNWm04zl%2Fkbs53FnZ%2FZO%2BldGbFP5aaP50cj41pigi8XFjF2zp8ivpgsFMFHp0GgrQZL4DuYGCE6f3pzoBnUwRB8sYi4QGKHf7b5d8HiHWpMBsPvLKDeFiHmVEPBN0yMJyMIUhfb6gXbMkr4xtq1J6Z36eLpmiDH508LNShbDzB4kTIATguNsBqA1CHElJDhGdCGWsDkYY%2FTJh3lUelu384yTlzrtgDWVaggvG8qhDnYcEwwWi0wET%2FTNTh9Gh%2FvVn7v%2B2I%2BHlpWXS59ORgfOr7UGRkVNMUAWPtCMnHdbjjATFNKJeKpdLZYQY0crDzLUvfbHxdqfllj6a7p2VVjUqyGhYwPpZFqxYlf6hZ%2F7X3c736%2Fv4LV1blv94gEvsAAAAASUVORK5CYII%3D" ID="rdf:#$CnoJ1">Get Bookmark Add-ons</A>
    <HR>
    <DT><H3 PERSONAL_TOOLBAR_FOLDER="true" ID="rdf:#$FvPhC3">Bookmarks Toolbar Folder</H3>
<DD>Add bookmarks to this folder to see them displayed on the Bookmarks Toolbar
    <DL><p>
        <DT><A HREF="http://en-US.www.mozilla.com/en-US/firefox/central/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAHWSURBVHjaYvz//z8DJQAggJiQOe/fv2fv7Oz8rays/N+VkfG/iYnJfyD/1+rVq7ffu3dPFpsBAAHEAHIBCJ85c8bN2Nj4vwsDw/8zQLwKiO8CcRoQu0DxqlWrdsHUwzBAAIGJmTNnPgYa9j8UqhFElwPxf2MIDeIrKSn9FwSJoRkAEEAM0DD4DzMAyPi/G+QKY4hh5WAXGf8PDQ0FGwJ22d27CjADAAIIrLmjo+MXA9R2kAHvGBA2wwx6B8W7od6CeQcggKCmCEL8bgwxYCbUIGTDVkHDBia+CuotgACCueD3TDQN75D4xmAvCoK9ARMHBzAw0AECiBHkAlC0Mdy7x9ABNA3obAZXIAa6iKEcGlMVQHwWyjYuL2d4v2cPg8vZswx7gHyAAAK7AOif7SAbOqCmn4Ha3AHFsIDtgPq/vLz8P4MSkJ2W9h8ggBjevXvHDo4FQUQg/kdypqCg4H8lUIACnQ/SOBMYI8bAsAJFPcj1AAEEjwVQqLpAbXmH5BJjqI0gi9DTAAgDBBCcAVLkgmQ7yKCZxpCQxqUZhAECCJ4XgMl493ug21ZD+aDAXH0WLM4A9MZPXJkJIIAwTAR5pQMalaCABQUULttBGCCAGCnNzgABBgAMJ5THwGvJLAAAAABJRU5ErkJggg==" ID="rdf:#$GvPhC3">Getting Started</A>
        <DT><A HREF="http://en-US.fxfeeds.mozilla.com/en-US/firefox/livebookmarks/" FEEDURL="http://en-US.fxfeeds.mozilla.com/en-US/firefox/headlines.xml" ID="rdf:#$HvPhC3">Latest Headlines</A>
    </DL><p>
    <HR>
    <DT><H3 ID="rdf:#$ZvPhC3">Mozilla Firefox</H3>
    <DL><p>
        <DT><A HREF="http://en-US.www.mozilla.com/en-US/firefox/help/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAHWSURBVHjaYvz//z8DJQAggJiQOe/fv2fv7Oz8rays/N+VkfG/iYnJfyD/1+rVq7ffu3dPFpsBAAHEAHIBCJ85c8bN2Nj4vwsDw/8zQLwKiO8CcRoQu0DxqlWrdsHUwzBAAIGJmTNnPgYa9j8UqhFElwPxf2MIDeIrKSn9FwSJoRkAEEAM0DD4DzMAyPi/G+QKY4hh5WAXGf8PDQ0FGwJ22d27CjADAAIIrLmjo+MXA9R2kAHvGBA2wwx6B8W7od6CeQcggKCmCEL8bgwxYCbUIGTDVkHDBia+CuotgACCueD3TDQN75D4xmAvCoK9ARMHBzAw0AECiBHkAlC0Mdy7x9ABNA3obAZXIAa6iKEcGlMVQHwWyjYuL2d4v2cPg8vZswx7gHyAAAK7AOif7SAbOqCmn4Ha3AHFsIDtgPq/vLz8P4MSkJ2W9h8ggBjevXvHDo4FQUQg/kdypqCg4H8lUIACnQ/SOBMYI8bAsAJFPcj1AAEEjwVQqLpAbXmH5BJjqI0gi9DTAAgDBBCcAVLkgmQ7yKCZxpCQxqUZhAECCJ4XgMl493ug21ZD+aDAXH0WLM4A9MZPXJkJIIAwTAR5pQMalaCABQUULttBGCCAGCnNzgABBgAMJ5THwGvJLAAAAABJRU5ErkJggg==" ID="rdf:#$22iCK1">Help and Tutorials</A>
        <DT><A HREF="http://en-US.www.mozilla.com/en-US/firefox/customize/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAHWSURBVHjaYvz//z8DJQAggJiQOe/fv2fv7Oz8rays/N+VkfG/iYnJfyD/1+rVq7ffu3dPFpsBAAHEAHIBCJ85c8bN2Nj4vwsDw/8zQLwKiO8CcRoQu0DxqlWrdsHUwzBAAIGJmTNnPgYa9j8UqhFElwPxf2MIDeIrKSn9FwSJoRkAEEAM0DD4DzMAyPi/G+QKY4hh5WAXGf8PDQ0FGwJ22d27CjADAAIIrLmjo+MXA9R2kAHvGBA2wwx6B8W7od6CeQcggKCmCEL8bgwxYCbUIGTDVkHDBia+CuotgACCueD3TDQN75D4xmAvCoK9ARMHBzAw0AECiBHkAlC0Mdy7x9ABNA3obAZXIAa6iKEcGlMVQHwWyjYuL2d4v2cPg8vZswx7gHyAAAK7AOif7SAbOqCmn4Ha3AHFsIDtgPq/vLz8P4MSkJ2W9h8ggBjevXvHDo4FQUQg/kdypqCg4H8lUIACnQ/SOBMYI8bAsAJFPcj1AAEEjwVQqLpAbXmH5BJjqI0gi9DTAAgDBBCcAVLkgmQ7yKCZxpCQxqUZhAECCJ4XgMl493ug21ZD+aDAXH0WLM4A9MZPXJkJIIAwTAR5pQMalaCABQUULttBGCCAGCnNzgABBgAMJ5THwGvJLAAAAABJRU5ErkJggg==" ID="rdf:#$32iCK1">Customize Firefox</A>
        <DT><A HREF="http://en-US.www.mozilla.com/en-US/firefox/community/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAHWSURBVHjaYvz//z8DJQAggJiQOe/fv2fv7Oz8rays/N+VkfG/iYnJfyD/1+rVq7ffu3dPFpsBAAHEAHIBCJ85c8bN2Nj4vwsDw/8zQLwKiO8CcRoQu0DxqlWrdsHUwzBAAIGJmTNnPgYa9j8UqhFElwPxf2MIDeIrKSn9FwSJoRkAEEAM0DD4DzMAyPi/G+QKY4hh5WAXGf8PDQ0FGwJ22d27CjADAAIIrLmjo+MXA9R2kAHvGBA2wwx6B8W7od6CeQcggKCmCEL8bgwxYCbUIGTDVkHDBia+CuotgACCueD3TDQN75D4xmAvCoK9ARMHBzAw0AECiBHkAlC0Mdy7x9ABNA3obAZXIAa6iKEcGlMVQHwWyjYuL2d4v2cPg8vZswx7gHyAAAK7AOif7SAbOqCmn4Ha3AHFsIDtgPq/vLz8P4MSkJ2W9h8ggBjevXvHDo4FQUQg/kdypqCg4H8lUIACnQ/SOBMYI8bAsAJFPcj1AAEEjwVQqLpAbXmH5BJjqI0gi9DTAAgDBBCcAVLkgmQ7yKCZxpCQxqUZhAECCJ4XgMl493ug21ZD+aDAXH0WLM4A9MZPXJkJIIAwTAR5pQMalaCABQUULttBGCCAGCnNzgABBgAMJ5THwGvJLAAAAABJRU5ErkJggg==" ID="rdf:#$42iCK1">Get Involved</A>
        <DT><A HREF="http://en-US.www.mozilla.com/en-US/firefox/about/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAHWSURBVHjaYvz//z8DJQAggJiQOe/fv2fv7Oz8rays/N+VkfG/iYnJfyD/1+rVq7ffu3dPFpsBAAHEAHIBCJ85c8bN2Nj4vwsDw/8zQLwKiO8CcRoQu0DxqlWrdsHUwzBAAIGJmTNnPgYa9j8UqhFElwPxf2MIDeIrKSn9FwSJoRkAEEAM0DD4DzMAyPi/G+QKY4hh5WAXGf8PDQ0FGwJ22d27CjADAAIIrLmjo+MXA9R2kAHvGBA2wwx6B8W7od6CeQcggKCmCEL8bgwxYCbUIGTDVkHDBia+CuotgACCueD3TDQN75D4xmAvCoK9ARMHBzAw0AECiBHkAlC0Mdy7x9ABNA3obAZXIAa6iKEcGlMVQHwWyjYuL2d4v2cPg8vZswx7gHyAAAK7AOif7SAbOqCmn4Ha3AHFsIDtgPq/vLz8P4MSkJ2W9h8ggBjevXvHDo4FQUQg/kdypqCg4H8lUIACnQ/SOBMYI8bAsAJFPcj1AAEEjwVQqLpAbXmH5BJjqI0gi9DTAAgDBBCcAVLkgmQ7yKCZxpCQxqUZhAECCJ4XgMl493ug21ZD+aDAXH0WLM4A9MZPXJkJIIAwTAR5pQMalaCABQUULttBGCCAGCnNzgABBgAMJ5THwGvJLAAAAABJRU5ErkJggg==" ID="rdf:#$52iCK1">About Us</A>
    </DL><p>
</DL><p>
```

I don't believe that those are my bookmarks but I could be wrong.  Thanks for the help.

---

### Post by jimrz on 2010-05-03
> **hortstu said:**
> jim,

this is what's in my bookmarks.html file...

```
<!DOCTYPE NETSCAPE-Bookmark-file-1>
<!-- This is an automatically generated file.
     It will be read and overwritten.
     DO NOT EDIT! -->
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=UTF-8">
<TITLE>Bookmarks</TITLE>
<H1>Bookmarks</H1>

<DL><p>
    <DT><A HREF="https://en-US.add-ons.mozilla.com/en-US/firefox/bookmarks/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAFo9M%2F3AAAABGdBTUEAANbY1E9YMgAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAPkSURBVHjaYmAAgrjyOnOGiKxqxT9%2F%2FvwHCCCGuNJKLpAo49KTL%2F5%2F%2F8PMABBADJFZFWwXnn%2F%2FDxJYeOLNf0aQ9AIg48%2Ff%2Fwwfvv1hAAggZpBAYlWdnrqJLcPVE4e%2Bsuy7%2FfH%2F%2B88%2FGdjY2Bj%2BcCqHMey6%2Ben%2F379%2F%2F%2F8B6unZ9ew%2Fy54jV249f6%2Bm9uXnX4Y9qyaoAAQAhAB7%2FwEAAAAAY3h%2BG1RdbeMMCgkB9%2Fr%2BAPL2%2FAC3vsyi5NG6YQFcbnwdZ3F44uru9gAAAQAAUjEVALPT7wDu9v4A5erz%2FgL19vr16PD6AAUHBgDu9PwA%2F%2F8AAO%2F2%2FgD0%2BP0A7e7x8QPYzsX38vj9g%2BPk6hkLFiAxy%2BP4AeHj5%2FXFtp9GonxaagII7AawXyprpf%2F%2FZ5L5%2Fe%2Fv9%2B%2Fff91ZN7nrG0icJSqrkknJxHm1h5Nl0J8%2F%2Fxg%2B%2FwDa%2Febzv39%2FWKQ2TG97ycIvq%2Bvn52oVxMHGxHDj8RcGQT4uEGZyCct98e3LL3YmJ2enNYxAi%2B48%2B8QQaizGIMLFBLaSlYWZgYWDWZaJhY2V%2BcvPfwz%2BeiIMf%2F%2F%2BY9CV4GAQ42Zh%2BPPvP8O%2Fv%2F%2BZmG7cff7u49c%2FDNtufGZgYmJiOHLvG8Pt1z8Yfv3%2Bz%2FDn19%2B3TCd2LNV7%2F%2FU3w7vPvxkWnHzDcOPFd4ZvQBPv3L79aM%2BS3nfMN88d%2BfyXkW0Lq6BiGAs7J8fHT9%2F%2FXTy%2BY82Lp0cdb5889hcgQJNU85JYFMXP%2B5aHqRmmZJ9kKMGAEBgtDCYYY6BFa%2BlrPc6yRf0LYYtZzG4YaNGibUNJVLuIcBNUTLMQM8ZoppdiaXnf9Xlf5z4ounDu4p57f%2Ff8Pt50SH9ZEfUuLehy93yMRBNroVAg6PV2yBbO9c94tK5v7suF3%2FlMs1o8oU27ltvIMic7fJv7uuqLJGa2UpPxlCILICBtGz1pYWooakeoDaTFgBtNWm04zl%2Fkbs53FnZ%2FZO%2BldGbFP5aaP50cj41pigi8XFjF2zp8ivpgsFMFHp0GgrQZL4DuYGCE6f3pzoBnUwRB8sYi4QGKHf7b5d8HiHWpMBsPvLKDeFiHmVEPBN0yMJyMIUhfb6gXbMkr4xtq1J6Z36eLpmiDH508LNShbDzB4kTIATguNsBqA1CHElJDhGdCGWsDkYY%2FTJh3lUelu384yTlzrtgDWVaggvG8qhDnYcEwwWi0wET%2FTNTh9Gh%2FvVn7v%2B2I%2BHlpWXS59ORgfOr7UGRkVNMUAWPtCMnHdbjjATFNKJeKpdLZYQY0crDzLUvfbHxdqfllj6a7p2VVjUqyGhYwPpZFqxYlf6hZ%2F7X3c736%2Fv4LV1blv94gEvsAAAAASUVORK5CYII%3D" ID="rdf:#$CnoJ1">Get Bookmark Add-ons</A>
    <HR>
    <DT><H3 PERSONAL_TOOLBAR_FOLDER="true" ID="rdf:#$FvPhC3">Bookmarks Toolbar Folder</H3>
<DD>Add bookmarks to this folder to see them displayed on the Bookmarks Toolbar
    <DL><p>
        <DT><A HREF="http://en-US.www.mozilla.com/en-US/firefox/central/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAHWSURBVHjaYvz//z8DJQAggJiQOe/fv2fv7Oz8rays/N+VkfG/iYnJfyD/1+rVq7ffu3dPFpsBAAHEAHIBCJ85c8bN2Nj4vwsDw/8zQLwKiO8CcRoQu0DxqlWrdsHUwzBAAIGJmTNnPgYa9j8UqhFElwPxf2MIDeIrKSn9FwSJoRkAEEAM0DD4DzMAyPi/G+QKY4hh5WAXGf8PDQ0FGwJ22d27CjADAAIIrLmjo+MXA9R2kAHvGBA2wwx6B8W7od6CeQcggKCmCEL8bgwxYCbUIGTDVkHDBia+CuotgACCueD3TDQN75D4xmAvCoK9ARMHBzAw0AECiBHkAlC0Mdy7x9ABNA3obAZXIAa6iKEcGlMVQHwWyjYuL2d4v2cPg8vZswx7gHyAAAK7AOif7SAbOqCmn4Ha3AHFsIDtgPq/vLz8P4MSkJ2W9h8ggBjevXvHDo4FQUQg/kdypqCg4H8lUIACnQ/SOBMYI8bAsAJFPcj1AAEEjwVQqLpAbXmH5BJjqI0gi9DTAAgDBBCcAVLkgmQ7yKCZxpCQxqUZhAECCJ4XgMl493ug21ZD+aDAXH0WLM4A9MZPXJkJIIAwTAR5pQMalaCABQUULttBGCCAGCnNzgABBgAMJ5THwGvJLAAAAABJRU5ErkJggg==" ID="rdf:#$GvPhC3">Getting Started</A>
        <DT><A HREF="http://en-US.fxfeeds.mozilla.com/en-US/firefox/livebookmarks/" FEEDURL="http://en-US.fxfeeds.mozilla.com/en-US/firefox/headlines.xml" ID="rdf:#$HvPhC3">Latest Headlines</A>
    </DL><p>
    <HR>
    <DT><H3 ID="rdf:#$ZvPhC3">Mozilla Firefox</H3>
    <DL><p>
        <DT><A HREF="http://en-US.www.mozilla.com/en-US/firefox/help/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAHWSURBVHjaYvz//z8DJQAggJiQOe/fv2fv7Oz8rays/N+VkfG/iYnJfyD/1+rVq7ffu3dPFpsBAAHEAHIBCJ85c8bN2Nj4vwsDw/8zQLwKiO8CcRoQu0DxqlWrdsHUwzBAAIGJmTNnPgYa9j8UqhFElwPxf2MIDeIrKSn9FwSJoRkAEEAM0DD4DzMAyPi/G+QKY4hh5WAXGf8PDQ0FGwJ22d27CjADAAIIrLmjo+MXA9R2kAHvGBA2wwx6B8W7od6CeQcggKCmCEL8bgwxYCbUIGTDVkHDBia+CuotgACCueD3TDQN75D4xmAvCoK9ARMHBzAw0AECiBHkAlC0Mdy7x9ABNA3obAZXIAa6iKEcGlMVQHwWyjYuL2d4v2cPg8vZswx7gHyAAAK7AOif7SAbOqCmn4Ha3AHFsIDtgPq/vLz8P4MSkJ2W9h8ggBjevXvHDo4FQUQg/kdypqCg4H8lUIACnQ/SOBMYI8bAsAJFPcj1AAEEjwVQqLpAbXmH5BJjqI0gi9DTAAgDBBCcAVLkgmQ7yKCZxpCQxqUZhAECCJ4XgMl493ug21ZD+aDAXH0WLM4A9MZPXJkJIIAwTAR5pQMalaCABQUULttBGCCAGCnNzgABBgAMJ5THwGvJLAAAAABJRU5ErkJggg==" ID="rdf:#$22iCK1">Help and Tutorials</A>
        <DT><A HREF="http://en-US.www.mozilla.com/en-US/firefox/customize/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAHWSURBVHjaYvz//z8DJQAggJiQOe/fv2fv7Oz8rays/N+VkfG/iYnJfyD/1+rVq7ffu3dPFpsBAAHEAHIBCJ85c8bN2Nj4vwsDw/8zQLwKiO8CcRoQu0DxqlWrdsHUwzBAAIGJmTNnPgYa9j8UqhFElwPxf2MIDeIrKSn9FwSJoRkAEEAM0DD4DzMAyPi/G+QKY4hh5WAXGf8PDQ0FGwJ22d27CjADAAIIrLmjo+MXA9R2kAHvGBA2wwx6B8W7od6CeQcggKCmCEL8bgwxYCbUIGTDVkHDBia+CuotgACCueD3TDQN75D4xmAvCoK9ARMHBzAw0AECiBHkAlC0Mdy7x9ABNA3obAZXIAa6iKEcGlMVQHwWyjYuL2d4v2cPg8vZswx7gHyAAAK7AOif7SAbOqCmn4Ha3AHFsIDtgPq/vLz8P4MSkJ2W9h8ggBjevXvHDo4FQUQg/kdypqCg4H8lUIACnQ/SOBMYI8bAsAJFPcj1AAEEjwVQqLpAbXmH5BJjqI0gi9DTAAgDBBCcAVLkgmQ7yKCZxpCQxqUZhAECCJ4XgMl493ug21ZD+aDAXH0WLM4A9MZPXJkJIIAwTAR5pQMalaCABQUULttBGCCAGCnNzgABBgAMJ5THwGvJLAAAAABJRU5ErkJggg==" ID="rdf:#$32iCK1">Customize Firefox</A>
        <DT><A HREF="http://en-US.www.mozilla.com/en-US/firefox/community/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAHWSURBVHjaYvz//z8DJQAggJiQOe/fv2fv7Oz8rays/N+VkfG/iYnJfyD/1+rVq7ffu3dPFpsBAAHEAHIBCJ85c8bN2Nj4vwsDw/8zQLwKiO8CcRoQu0DxqlWrdsHUwzBAAIGJmTNnPgYa9j8UqhFElwPxf2MIDeIrKSn9FwSJoRkAEEAM0DD4DzMAyPi/G+QKY4hh5WAXGf8PDQ0FGwJ22d27CjADAAIIrLmjo+MXA9R2kAHvGBA2wwx6B8W7od6CeQcggKCmCEL8bgwxYCbUIGTDVkHDBia+CuotgACCueD3TDQN75D4xmAvCoK9ARMHBzAw0AECiBHkAlC0Mdy7x9ABNA3obAZXIAa6iKEcGlMVQHwWyjYuL2d4v2cPg8vZswx7gHyAAAK7AOif7SAbOqCmn4Ha3AHFsIDtgPq/vLz8P4MSkJ2W9h8ggBjevXvHDo4FQUQg/kdypqCg4H8lUIACnQ/SOBMYI8bAsAJFPcj1AAEEjwVQqLpAbXmH5BJjqI0gi9DTAAgDBBCcAVLkgmQ7yKCZxpCQxqUZhAECCJ4XgMl493ug21ZD+aDAXH0WLM4A9MZPXJkJIIAwTAR5pQMalaCABQUULttBGCCAGCnNzgABBgAMJ5THwGvJLAAAAABJRU5ErkJggg==" ID="rdf:#$42iCK1">Get Involved</A>
        <DT><A HREF="http://en-US.www.mozilla.com/en-US/firefox/about/" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAHWSURBVHjaYvz//z8DJQAggJiQOe/fv2fv7Oz8rays/N+VkfG/iYnJfyD/1+rVq7ffu3dPFpsBAAHEAHIBCJ85c8bN2Nj4vwsDw/8zQLwKiO8CcRoQu0DxqlWrdsHUwzBAAIGJmTNnPgYa9j8UqhFElwPxf2MIDeIrKSn9FwSJoRkAEEAM0DD4DzMAyPi/G+QKY4hh5WAXGf8PDQ0FGwJ22d27CjADAAIIrLmjo+MXA9R2kAHvGBA2wwx6B8W7od6CeQcggKCmCEL8bgwxYCbUIGTDVkHDBia+CuotgACCueD3TDQN75D4xmAvCoK9ARMHBzAw0AECiBHkAlC0Mdy7x9ABNA3obAZXIAa6iKEcGlMVQHwWyjYuL2d4v2cPg8vZswx7gHyAAAK7AOif7SAbOqCmn4Ha3AHFsIDtgPq/vLz8P4MSkJ2W9h8ggBjevXvHDo4FQUQg/kdypqCg4H8lUIACnQ/SOBMYI8bAsAJFPcj1AAEEjwVQqLpAbXmH5BJjqI0gi9DTAAgDBBCcAVLkgmQ7yKCZxpCQxqUZhAECCJ4XgMl493ug21ZD+aDAXH0WLM4A9MZPXJkJIIAwTAR5pQMalaCABQUULttBGCCAGCnNzgABBgAMJ5THwGvJLAAAAABJRU5ErkJggg==" ID="rdf:#$52iCK1">About Us</A>
    </DL><p>
</DL><p>
```

I don't believe that those are my bookmarks but I could be wrong.  Thanks for the help.

you don't need to open the file, just paste into ~/>mozilla/firefox in Lucid ( if you like, re-name the one that is already there to something like bookmarks.html-bak jic) then the next time you open FF you should have your Hardy bookmarks.

you might also consider getting the Xmarks FF extention which will backup your bookmarks on line and even sync them across various machines / installations

---

### Post by TransitMan on 2010-05-03
In Firefox, go to Bookmarks -> Organize Bookmarks
New window opens, along the top you'll see a heading marked import export.
Export your bookmarks in .html format somewhere on your partitions.

Then go to Lucid, open Firefox, and repaet the process, but instead of exporting you want to import the .html file where you saved it previously.

---

### Post by lovinglinux on 2010-05-04
> **jimrz said:**
> 2] for FF your bookmarks are contained in ~/.mozilla/firefox/bookmarks.html, just copy it from Hardy  and paste to Lucid, as above.

No, they are not. That is an old file from Firefox 2 kept for compatibility. Bookmarks are actually stored in a database file - places.sqlite

To backup you can simply copy that file to the new profile or you can export a backup (json file or html). See the Backup section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by jimrz on 2010-05-04
> **lovinglinux said:**
> No, they are not. That is an old file from Firefox 2 kept for compatibility. Bookmarks are actually stored in a database file - places.sqlite

To backup you can simply copy that file to the new profile or you can export a backup (json file or html). See the Backup section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

thanks for the info, and my apologies for the outdated info I posted

---

