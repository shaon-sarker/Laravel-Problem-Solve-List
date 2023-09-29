
## Authors

- [@shaon](https://github.com/shaon-sarker)


# Multivendor Ecommerce

Problems I faced while doing the project in Laravel.



## Problem 01

Eloquent relationship with Category and Subcategory

Category model

```bash
   public function subcategories()
    {
        return $this->hasMany(Subcategory::class);
    }
```
Sub-Category model

```bash
   public function category()
    {
        return $this->belongsTo(Category::class,'category_id');
    }
 ```
 Sub-category Controller
```bash
   public function index()
    {
    $subcategorys = Subcategory::select(['id','category_id','subcategory_name','subcategory_slug'])->with('category')->paginate(3);
    return view('admin.pages.subcategory.index',compact('subcategorys'));
    }
 ```
  subcategory/index.blade.php 
```bash
  {{ $subcategory->category->category_name}}
 ```