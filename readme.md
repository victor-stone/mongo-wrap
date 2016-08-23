
mongo-db wrapper server middleware

Think of this as a mini-mongoose wrapper that turns a db into an object addressable api.


````javascript

  var epxress = require('express');
  var mwrap  = require('mongo-wrap');

  var meta = {
      dbName: 'volunteers',
      collections: [ 'volunteer' ]
  };

  mwrap.init( meta.dbName, meta.collections ).then( (db) => {
    const app  = express();
    app.get( '/list-volunteers', (req,res) => {
        res.json( db.volunteer.find().toArray() )
      });
    const port = process.env.PORT || 3000;
    app.listen( port, () => console.log('Server listening on port ' + port) );
  });

````


