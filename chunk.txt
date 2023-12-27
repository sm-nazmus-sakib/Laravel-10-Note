Laravel-10-Note
************************************
1. Chunk Method
===========================================
LaravelPHPServer Side Programming. 
If your database table has lots of data, chunk() method is the best to use. 
The chunk() method can be used on the DB facade and also on Eloquent models. 
The chunk() takes care of fetching a small amount of data at a time and the result is present inside the closure for processing.
-----------------------------------------------
-> From Controller File
 public function chunkdata(){
            $students = DB::table('students')->orderBy('id')
              ->chunkById(2, function($students){
                    echo "<div style = 'border: 1px solid red';>";
                    foreach ($students as $student) {
                       echo $student->name . "<br>";
                    }
                    echo "</div>";
              });
        }
---------------------------------------------------------
public function chunkdata(){
            $students = DB::table('students')->orderBy('id')
              ->chunkById(2, function($students){
                    
                    foreach ($students as $student) {
                        $students = DB::table('students')
                        ->where('id', $student->id)
                        ->update(['stutas'=> true ]);
                    }
                    
              });
        }


       
