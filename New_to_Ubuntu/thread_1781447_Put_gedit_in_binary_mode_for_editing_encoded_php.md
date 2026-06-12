---
title: "Put gedit in binary mode for editing encoded php?"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by iansane on 2011-06-13
Hi,

I had an error on a web site in a file that contained some encoded binary from phpshield. Simply opening the file and changing part of the non encoded php and then saving it caused gedit to add new line character at the end of every line including several hundred in the encoded part. This makes the entire site not work because the encoded part has to pass the phpshield check.

My question, is there a way to put gedit in binary mode so it won't try to add any formatting at all to a text file unless I specifically add a new line by hitting the enter key?

For some added info, when I use the find option it doesn't find any /n entries but I know you can use the find replace to put a new line in by using /n as the replacement. Just doesn't seem to work as the "find what" parameter

Thanks

---

### Post by hakermania on 2011-06-13
Hello, I don't know about the main problem but its '\n', no '/n'

---

### Post by iansane on 2011-06-13
> **hakermania said:**
> Hello, I don't know about the main problem but its '\n', no '/n'

yeah typo there, thanks.

Still can only find one instance of a new line and it's not in the encoded part.

Here's a sample to explain better what it did.

Before gedit:
```

'FZxAJacVCU7JgYeJuz06tFRhFGWWXFAVOPfIJkJIncpqwtuaICivyq3D2ymDbmOimFP25LKBHqkLGLq/Y04Q7GNCSdcy+aIxU5qX/AZ4bs79GKB2CHQwZNK9ClkZut8NIHAwiAz8O4ArQpG8hRq5qjUAAAB4IgIAxmYKwX2kIlJ+7AaqDjJ4tk1v+0a69kNRXiHovA9bq5/8ax/pfqPAW6NoTW6i3qhz/E/gyNMaZu4ZPBthQWLLktNf9J97WK9ueTj+9RmFHYhwmTN7iNVnP8W2kentlKNdX6dCAcgKrxcFv+glfM0xZ+0VvUm4v+NBZYwmqKiw2Ey0BSEvAvv/uLqoYhRZTodJTHAv2yk7Ilcz585w7uR8cIMSvhRvPF6Wj0HkVhmGwBiVA9LXJa8sOoQL9kNnuiyXLoy7djyfAJRzE/56lpAtgXvHw9GDp2mPRyocfo6jPNt99rVz1PXkUolwg71kCYAIXZ+9ShCZDYpyzWX8scsdJ2yB6JLGmFJEfJNgmHnxTGIrjBB80LhIAIoF12yZurweJ6pPyNsGS0sIyrmm1Iv/dX4jB5oaGzkjdmZ3qQR9kbqbTombER0IbX/AQCHPBGMNv9d77TCiMJpBL4+helG5Jxa0jbw+fUzZTiSB4gfR1mZU9Tz7DQG8fWfjgg70kPxRIstQFDc7WjLjCX/kjR+q/D7gAIXGtcdSB1n6y6XN2jryLlMXc0EshWEOhr3uyoVjLvEM04QDb8PELrGgxok01H5/Bks+M'


```

After gedit:
```
'FZxAJacVCU7JgYeJuz06tFRhFGWWXFAVOPfIJkJ
IncpqwtuaICivyq3D2ymDbmOimFP25LKBHqkLGLq/Y04Q7GNCSdcy+aIx
U5qX/AZ4bs79GKB2CHQwZNK
9ClkZut8NIHAwiAz8O4ArQpG8hRq5qjUAAAB4IgIAxmYKwX2kIlJ+7AaqDjJ4tk1v+0a69kNRXiHovA9bq5/8ax/pfqPAW6NoTW6i3qhz/E/gyNMaZu4ZPBthQWLLktNf9J97WK9ueTj+9RmFHYhwmTN7iNVnP8W2kentlKNdX6dCAcgKrxcFv+glfM0
xZ+0VvUm4v+NBZYwmqKiw2Ey0BSEvAvv/uLqoYhRZTodJTHAv2yk7Ilcz585w7uR8cIMSvhRvPF6Wj0HkVhmGwBiVA9LXJa8sOoQL9kNnuiyXLoy7djyfAJRzE/56lpAtgXvHw9GDp2mPRyocfo6jPNt99rVz1PXkUolwg
71kCYAIXZ+9ShCZDYpyzWX8scsdJ2yB6JLGmFJEfJNgmHnxTGIrjBB80LhIAIoF12yZurweJ6pPyNsGS0sIyrmm1Iv/dX4jB5oaGzkjdmZ3qQR9kbqbTombER0IbX/AQCHPBGMNv9d77TCiMJpBL4+helG5Jxa0jbw+fUzZTiSB4gf
R1mZU9Tz7DQG8fWfjgg70kPxRIstQFDc7WjLjCX/kjR+q/D7gAIXGtcdSB1n6y6XN2jryLlMXc0EshWEOhr3uyoVjLvEM04QDb8PELrGgxok01H5/Bks+M'


```

Looks like it just randomly placed new lines where it thought it should instead of leaving it alone. I didn't even go near the part in quotes that got messed up because I knew better than to mess with it.

Also I've tried searchin for \r\n for windows new lines and don't find any.

And it won't allow me to manually remove the lines to put the text back together again.

---

### Post by iansane on 2011-06-13
I should add that when I open the same file in scite from the original file it keeps it all in one super long line like it was originally. This is the functionality I'm hoping to find in gedit

---

### Post by iansane on 2011-06-13
I just figured it out. In preferences the first two under text wrapping were enabled.

I disabled them and it opens the file with the encoded part all in one super long line. Only problem now is that it freezes up and takes forever because it is trying to load hundreds of lines into one long string. I would think it was memory related(low system ram) or cpu related but scite on the same system doesn't seem to have that problem though. It's a little slow but doesn't freeze up.

Just when I thought I had the perfect code editor, had to go and find a random flaw (not the text wrap part but the freezing part).

---

