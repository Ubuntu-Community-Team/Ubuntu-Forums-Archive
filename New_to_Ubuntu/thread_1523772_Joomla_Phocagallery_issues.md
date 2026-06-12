---
title: "Joomla Phocagallery issues"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by susanpenter on 2010-07-04
Hi guys, having got sick of waiting weeks for help on the Joomla and phocagallery forums I thought someone on this forum is bound to be able to help me with this web issue:

[http://www.wiltshire-opc.org.uk/information/index.php?option=com_phocagallery&view=category&id=45:aldbourne&Itemid=69](http://www.wiltshire-opc.org.uk/information/index.php?option=com_phocagallery&view=category&id=45:aldbourne&Itemid=69)

on each page of the photo gallery on my site, like the one above, I am seeing this error:

Notice: Undefined variable: itemId in /home/sites/wiltshire-opc.org.uk/public_html/information/components/com_phocagallery/views/category/view.html.php on line 819

When I go into the code for the line I see this:
```

if ($itemId > 0 && $display_categories_back_button_cv == 1) {
					$itemsCV[$iCV] 						= new JObject();
					$itemsCV[$iCV]->link 				= $backLink;
					$itemsCV[$iCV]->title				= JTEXT::_('Category List');
					$itemsCV[$iCV]->item_type 			= "categorieslistcv";
					$itemsCV[$iCV]->linkthumbnailpath	= PhocaGalleryImageFront::displayBackFolder('medium', 1);
					$itemsCV[$iCV]->extm				= $itemsCV[$iCV]->linkthumbnailpath;
					$itemsCV[$iCV]->exts				= $itemsCV[$iCV]->linkthumbnailpath;
					$itemsCV[$iCV]->numlinks = 0;// We are in category view
					$itemsCV[$iCV]->link 				= JRoute::_( $itemsCV[$iCV]->link );
					$itemsCV[$iCV]->type				= 3;
					$itemsCV[$iCV]->altvalue			= '';
					$iCV++;

```

I would be very grateful if some kind person out there could offer some advice.

---

