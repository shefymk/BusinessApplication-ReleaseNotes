---

title: Resource image improvements for Universal Resource Scheduling
description: Resouce images used to get cut off dependning on row height; this has been updated.
author: krbjoran
manager: shellyhaverkamp
ms.date: 06/01/2018
ms.topic: article
ms.prod: 
ms.service: business-applications
ms.technology: 
ms.author: krbjoran
audience: end user

---

# Remove resourced image from schedule board when the row height cuts off image

[!include[banner](../../includes/banner.md)]

In the previous release, we released a feature that allows you to shrink the height of each resource row, thereby enabling resource managers to [view more resources on the board in a single glance](https://blogs.msdn.microsoft.com/crm/2018/04/02/whats-new-in-universal-resource-scheduling-for-dynamics-365-april-2018-update/#displaymoreresources). However, depending on the row height, the resource image got cut off. Now, we simply remove the resource image from the resource cell when the height is too small. 

For new organizations, this functionality will be included out of the box. For existing organizations, if you have yet to customize your resource template, you will also receive this functionality out of the box. For existing organizations that already customized the resource template, you will need to add the following to your resource template for the schedule board, and for the schedule assistant.

```
<div class='resource-card-wrapper {{iif ResourceCellSelected "resource-cell-selected" ""}} {{iif ResourceUnavailable "resource-unavailable" ""}} {{iif IsMatchingAvailability "availability-match" ""}}'>
{{#if (or (eq (is-sa-grid-view) true) (eq (is-row-small) false)) }}
{{#if imagepath}}
<img class='resource-image' src='{{client-url}}{{imagepath}}' />
{{else}}
<div class='resource-image unknown-resource'></div>
{{/if}}
{{/if}}
```
