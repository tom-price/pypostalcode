###pypostalcode

This is a fork of Nathan Van Gheem's excellent pyzipcode package.  The zipcode database has been replaced with Canadian cities and their postal codes.  The general usage is the same.
        
Canadian postal codes are six characters with this format: A1A 1A1, where A is a letter and 1 is a digit, with a space separating the third and fourth characters. The first three digits are the forward sortation area (FSA), and the last three are the local delivery unit (LDU).  

This module only uses the FSA designator for location. There are over 800,000 FSA+LDU combinations, but the 1,620 unique FSA values provide enough resolution for most applications.

To use, run

```
pip install pypostalcode
```

Basic usage (copied from the pyzipcode docs):


```
	>>> from pypostalcode import PostalCodeDatabase
	>>> pcdb = PostalCodeDatabase()
	>>> location = pcdb['V5K']
	>>> location.postalcode
	u'V5K'
	>>> location.city
	u'Vancouver (North Hastings- Sunrise)'
	>>> location.province
	u'British Columbia'
	>>> location.longitude
	49.293
	>>> location.latitude
	-123.0489
	>>> location.timezone
	-8
```	

Get a list of postal codes given a radius in kilometers:

```	
	>>> from pypostalcode import PostalCodeDatabase
	>>> pcdb = PostalCodeDatabase()
	>>> results = pcdb.get_postalcodes_around_radius('T3Z', 25)
	>>> for r in results:
	>>>     ''.join([r.postalcode, ": ", r.city, ", ", r.province])
        u'T3B: Calgary (Montgomery / Bowness / Silver Springs / Greenwood), Alberta'
	u'T3G: Calgary (Hawkwood / Arbour Lake / Royal Oak / Rocky Ridge), Alberta'
	u'T3H: Calgary (Discovery Ridge / Signal Hill / Aspen Woods / Patterson / Cougar Ridge), Alberta'
	u'T3L: Calgary (Tuscany / Scenic Acres), Alberta'
	u'T3R: Calgary Northwest, Alberta'
	u'T3Z: Redwood Meadows, Alberta'
	u'T4C: Cochrane, Alberta'
```
