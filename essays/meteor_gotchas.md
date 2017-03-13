---
layout: essay
type: essay
title: Piecing it Together with Meteor
date: 2017-03-09
published: false
labels:
  - Software Engineering
  - Meteor
---




## Meteor

I recently started using Meteor, which is a JavaScript web-framework that uses  Node.js and integrates with MongoDB in place of SQL.  Wrapping my head around using it has been a lot to take in and has not been without any problems.  I particularly had a problem with making my web-pages publish properly.


## Match It

In one exercise or nstance of working with Digits, I couldn't figure out why my web-page content was not appearing as expected.  A guide was provided to make sure my code was correct.  I kept trying to find mismatches line-by-line and eventually found that my problem was simply that my naming of variables needed to be consistent and that 'SimpleSchema' needed to remain as 'SimpleSchema' since it borrowed from a template.  After applying the appropriate changes, my web-pages were able to sync-up and get published as expected.

```javascript
import { Mongo } from 'meteor/mongo';
import { SimpleSchema } from 'meteor/aldeed:simple-schema';

/* eslint-disable object-shorthand */

export const Stuff = new Mongo.Collection('Stuff');

/**
 * Create the schema for Stuff
 */
export const StuffSchema = new SimpleSchema({
  name: {
    label: 'Name',
    type: String,
    optional: false,
    max: 20,
    autoform: {
      group: 'Stuff',
      placeholder: 'Bicycle',
    },
  },
  quantity: {
    label: 'Quantity',
    type: Number,
    optional: false,
    autoform: {
      group: 'Stuff',
      placeholder: '3',
    },
  },
});

Stuff.attachSchema(StuffSchema);
```

## Link It

Another problem I encountered is how whatever I expected to have published on my web-page did not appear, even if all the coding for it seemed correct.  After double-checking to make sure that everything was coded correctly, I realized that the reason it wasn't being published is because my HTML or JavaScript files needed to be imported.  After this experience, I didn't have any trouble with making sure my pages were properly linked together and being imported.
