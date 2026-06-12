---
title: "sites that won't save your login and password"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by northwestuntu on 2009-07-26
im using firefox and there are some sites like verizon wirless that i can't get firefox to save the login and password.  i have to type them in everytime.  most the time firefox will ask me if i want to save the info.

is there a extension that will make firefox save login and passwords for any sites.  i couldn't find one.

thanks

---

### Post by QIII on 2009-07-26
Is it possible that at some point you were asked and responded "never for this site"?

Check the Security tab in Preferences.

Look at "Remember passwords for sites" and see if it is enabled.

Then click the "Exceptions" button and see if the site you want to remember your passord is there.  If so, remove it.

---

### Post by ftabor on 2009-07-26
There are a lot of websites that do not set the cookies, or actively block saving your passwords.  Banks in particular.

You can try this code, copy and paste it into the address bar when you are at the Verizon site.  Hit the return key before you enter your user/password.  If this works for you, you can create a bookmark for it and use it on other sites.  

It depends on how the site is blocking whether it will work for you or not.

```
javascript:(function(){var%20ca,cea,cs,df,dfe,i,j,x,y;function%20n(i,what){return%20i+%22%20%22+what+((i==1)?%22%22:%22s%22)}ca=cea=cs=0;df=document.forms;for(i=0;i<df.length;++i){x=df[i];dfe=x.elements;if(x.onsubmit){x.onsubmit=%22%22;++cs;}if(x.attributes[%22autocomplete%22]){x.attributes[%22autocomplete%22].value=%22on%22;++ca;}for(j=0;j<dfe.length;++j){y=dfe[j];if(y.attributes[%22autocomplete%22]){y.attributes[%22autocomplete%22].value=%22on%22;++cea;}}}alert(%22Removed%20autocomplete=off%20from%20%22+n(ca,%22form%22)+%22%20and%20from%20%22+n(cea,%22form%20element%22)+%22,%20and%20removed%20onsubmit%20from%20%22+n(cs,%22form%22)+%22.%20After%20you%20type%20your%20password%20and%20submit%20the%20form,%20the%20browser%20will%20offer%20to%20remember%20your%20password.%22)})();
```

---

### Post by northwestuntu on 2009-07-26
> **QIII said:**
> Is it possible that at some point you were asked and responded "never for this site"?

Check the Security tab in Preferences.

Look at "Remember passwords for sites" and see if it is enabled.

Then click the "Exceptions" button and see if the site you want to remember your passord is there.  If so, remove it.

yep already checked that.

---

### Post by northwestuntu on 2009-07-26
> **ftabor said:**
> There are a lot of websites that do not set the cookies, or actively block saving your passwords.  Banks in particular.

You can try this code, copy and paste it into the address bar when you are at the Verizon site.  Hit the return key before you enter your user/password.  If this works for you, you can create a bookmark for it and use it on other sites.  

It depends on how the site is blocking whether it will work for you or not.

```
javascript:(function(){var%20ca,cea,cs,df,dfe,i,j,x,y;function%20n(i,what){return%20i+%22%20%22+what+((i==1)?%22%22:%22s%22)}ca=cea=cs=0;df=document.forms;for(i=0;i<df.length;++i){x=df[i];dfe=x.elements;if(x.onsubmit){x.onsubmit=%22%22;++cs;}if(x.attributes[%22autocomplete%22]){x.attributes[%22autocomplete%22].value=%22on%22;++ca;}for(j=0;j<dfe.length;++j){y=dfe[j];if(y.attributes[%22autocomplete%22]){y.attributes[%22autocomplete%22].value=%22on%22;++cea;}}}alert(%22Removed%20autocomplete=off%20from%20%22+n(ca,%22form%22)+%22%20and%20from%20%22+n(cea,%22form%20element%22)+%22,%20and%20removed%20onsubmit%20from%20%22+n(cs,%22form%22)+%22.%20After%20you%20type%20your%20password%20and%20submit%20the%20form,%20the%20browser%20will%20offer%20to%20remember%20your%20password.%22)})();
```

ill give that a shot

---

