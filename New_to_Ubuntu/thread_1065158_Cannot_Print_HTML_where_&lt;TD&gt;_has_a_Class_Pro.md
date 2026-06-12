---
title: "Cannot Print HTML where &lt;TD&gt; has a Class Property ??"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-09
Hi,

Odd problem, I'm able to print, but tables that have Table Data Tags <TD></TD> with a CLASS property refuse to print (or Preview).

It's as if nothing is there.

Anyone know what could cause this?

Misty

---

### Post by lykwydchykyn on 2009-02-09
Depends on the style sheet.  Style sheets can have different properties assigned to a class depending on if it's being viewed on a screen, printed, etc.

So, it's possible that the style sheet for whatever you're printing defines that class of <TD> as "display: none" for the printing medium.

Make sense?

---

### Post by mistypotato on 2009-02-09
Here's the style sheet that defines the classes for the printout in question.

I don't see anything t6hat would cause that do you?

Could it be my computer lacks the Arial Font ??




[COLOR="Green"]
.Receipts {	font-family: Arial, Helvetica, sans-serif;
}
.Borders {
	border: thin solid #CCCCCC;
}
.SmallBld {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 11px;
	font-weight: bold;
	border: thin solid #CCCCCC;
	height: 15px;
	line-height: 22px;


}
.ContentTextSmall {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 10px;
	line-height: 14px;
	border: thin solid #CCCCCC;
}
.SummaryBold11pt {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 11px;
	font-weight: bold;
	border: thin solid #333333;
}
.Context10ptNml {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 11px;
	border: thin solid #CCCCCC;
	line-height: 14px;

}
.smalltextblkbrdr {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 10px;
	border: 1px solid #000000;
	line-height: 22px;

}
.Boldsmalltextblkbrdr {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 11px;
	line-height: 22px;
	font-weight: bold;
	border: thin solid #333333;
}
.Smalltxtnoborder {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 9px;
}[/COLOR]

---

### Post by daqron on 2009-02-09
mistypotato:

Here are some silly questions that it might be helpful for you to answer so that I and others can be helpful ...
[LIST]
[*]Which class(es) are affected? Do none of the classes you posted print properly?
[*]When you say "it's as if there's nothing there" do you mean there is blank space where the table should be (as if you were printing white text on a white background), or that the table seems to be completely ignored when you try to print?
[*]Do you have a sample of the HTML or (better) a link to the offending page?
[*]If you print to PDF do the tables show up?
[*]Do the missing tables show up in the print preview?
[*]Have you tried multiple browsers? Which ones have this problem?
[/LIST]

> **mistypotato said:**
> Could it be my computer lacks the Arial Font ??
Probably not since the stylesheet defines an alternate font and generic font family.

---

### Post by Paqman on 2009-02-09
Is that definitely the stylesheet for print?

---

