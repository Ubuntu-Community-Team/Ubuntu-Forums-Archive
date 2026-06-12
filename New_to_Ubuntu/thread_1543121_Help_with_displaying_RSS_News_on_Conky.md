---
title: "Help with displaying RSS News on Conky?"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by pkjm17 on 2010-07-31
For some reason, my script in conky for displaying the BBC News has stopped working. It doesn't display any news. Is there something I'm missing or is there a new link? This is what I have,

```
NEWS ${hr 2}
${font LucidaGrande:size=10}${color ffffff}BBC News | World
${font}${rss http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml 10 item_title 0}
${font}${rss http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml 10 item_title 1}
${font}${rss http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml 10 item_title 2}
${font}${rss http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml 10 item_title 3}
${font}${rss http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml 10 item_title 4}
${endif}
```

---

### Post by corrytonapple on 2010-08-04
Try posting here:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

