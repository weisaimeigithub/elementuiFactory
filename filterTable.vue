<template>
  <indexList :data="tableData" :th-list="thList">
    <!-- 日期select搜索 -->
    <template #dateHeader>
      <el-select ref="dateSelectRef" v-model="tableSearchParams.date" value-key="createdByKey" filterable
        placeholder="Alldate" @change="handleSelect">
        <template slot="prefix">
          <i class="el-icon-search" />
        </template>
        <el-option key="all" :label="'allDate'" :value="'allDate'" />
        <el-option v-for="option in dateOptions" :key="`${option.value} ${option.label}`" :label="option.label.trim()"
          :value="option.label" />
      </el-select>
    </template>
    <!-- 姓名select搜索 -->
    <template #nameHeader>
      <el-select ref="nameSelectRef" v-model="tableSearchParams.name" value-key="nameKey" filterable
        placeholder="Allname" @change="handleSelect">
        <template slot="prefix">
          <i class="el-icon-search" />
        </template>
        <el-option key="all" :label="'allName'" :value="'allName'" />
        <el-option v-for="option in nameOptions" :key="`${option.value} ${option.label}`" :label="option.label.trim()"
          :value="option.label" />
      </el-select>
    </template>
    <!-- 省select搜索 -->
    <template #provinceHeader>
      <el-select ref="provinceSelectRef" v-model="tableSearchParams.province" value-key="provinceKey" filterable
        placeholder="Allprovince" @change="handleSelect">
        <template slot="prefix">
          <i class="el-icon-search" />
        </template>
        <el-option key="all" :label="'allProvince'" :value="'allProvince'" />
        <el-option v-for="option in provinceOptions" :key="`${option.value} ${option.label}`"
          :label="option.label.trim()" :value="option.label" />
      </el-select>
    </template>
    <!-- city select搜索 -->
    <template #cityHeader>
      <el-select ref="citySelectRef" v-model="tableSearchParams.city" value-key="cityKey" filterable
        placeholder="Allcity" @change="handleSelect">
        <template slot="prefix">
          <i class="el-icon-search" />
        </template>
        <el-option key="all" :label="'allCity'" :value="'allCity'" />
        <el-option v-for="option in cityOptions" :key="`${option.value} ${option.label}`" :label="option.label.trim()"
          :value="option.label" />
      </el-select>
    </template>
    <!-- addre select搜索 -->
    <template #addressHeader>
      <el-select ref="addressSelectRef" v-model="tableSearchParams.address" value-key="addressKey" filterable
        placeholder="Alladdress" @change="handleSelect">
        <template slot="prefix">
          <i class="el-icon-search" />
        </template>
        <el-option key="all" :label="'allAddress'" :value="'allAddress'" />
        <el-option v-for="option in addressOptions" :key="`${option.value} ${option.label}`"
          :label="option.label.trim()" :value="option.label" />
      </el-select>
    </template>
    <!-- zip select搜索 -->
    <template #zipHeader>
      <el-select ref="zipSelectRef" v-model="tableSearchParams.zip" value-key="zipKey" filterable placeholder="Allzip"
        @change="handleSelect">
        <template slot="prefix">
          <i class="el-icon-search" />
        </template>
        <el-option key="all" :label="'allZip'" :value="'allZip'" />
        <el-option v-for="option in zipOptions" :key="`${option.value} ${option.label}`" :label="option.label.trim()"
          :value="option.label" />
      </el-select>
    </template>
  </indexList>
</template>

<script>
// filter-method 这一期的业务 不需要 模糊搜索的 不需要 自带的
// 带一个前端是否可以实现的模糊查询 这个方案去问产品
// @visible-change 点开下拉框调用 接口
// @change 这个自己过滤tablelist
import indexList from '@/ggcomponents/LPList/indexList.vue';
export default {
  components: {
    indexList
  },
  data() {
    return {
      dateOptions: [],
      nameOptions: [],
      provinceOptions: [],
      cityOptions: [],
      addressOptions: [],
      zipOptions: [],
      tableSearchParams: {
        date: '',
        name: '',
        province: '',
        city: '',
        address: '',
        zip: ''
      },
      tableData: [{
        date: '2016-05-02',
        name: '王小1',
        province: '上海',
        city: '上海',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: '200331'
      }, {
        date: '2016-05-04',
        name: '魏小2',
        province: '上海',
        city: '上海',
        address: '上海金沙江路 1517 弄',
        zip: '200332'
      }, {
        date: '2016-05-01',
        name: '刘小3',
        province: '山西',
        city: '大同',
        address: '山西大同金沙江路 1519 弄',
        zip: '200333'
      }, {
        date: '2016-05-03',
        name: '李小4',
        province: '重庆',
        city: '重庆',
        address: '重庆市金沙江路 1516 弄',
        zip: '200334'
      },
      {
        date: '2016-05-03',
        name: '孙小5',
        province: '重庆',
        city: '重庆',
        address: '重庆市金沙江路 1516 弄',
        zip: '200334'
      },
      {
        date: '2016-05-01',
        name: '魏小2',
        province: '辽宁',
        city: '丹东',
        address: '辽宁丹东金沙江路 1517 弄',
        zip: '200332'
      },
      {
        date: '2016-05-02',
        name: '魏小2',
        province: '辽宁',
        city: '丹东',
        address: '辽宁丹东金沙江路 1517 弄',
        zip: '200332'
      },
      ],
      thList: [{
        value: 'date',
        label: '日期',
        minWidth: 170,
        showOverflowTooltip: true,
        fixed: true,
        slotHeader: true
      },
      {
        value: 'name',
        label: '姓名',
        minWidth: 170,
        showOverflowTooltip: true,
        fixed: true,
        slotHeader: true
      },
      {
        value: 'province',
        label: '省份',
        minWidth: 170,
        showOverflowTooltip: true,
        fixed: true,
        slotHeader: true
      },
      {
        value: 'city',
        label: '市区',
        minWidth: 170,
        showOverflowTooltip: true,
        fixed: true,
        slotHeader: true
      },
      {
        value: 'address',
        label: '地址',
        minWidth: 170,
        showOverflowTooltip: true,
        fixed: true,
        slotHeader: true
      },
      {
        value: 'zip',
        label: '邮编',
        minWidth: 170,
        showOverflowTooltip: true,
        fixed: true,
        slotHeader: true
      }
      ],
      tableSearchList: [],
      tableDataNew: [],
      length: 0
    }
  },

  computed: {

  },
  created() {
    this.getdateOptions(),
      this.getnameOptions(),
      this.getprovinceOptions(),
      this.getcityOptions(),
      this.getaddressOptions(),
      this.getzipOptions(),
      this.tableDataNew = this.tableData
  },

  methods: {
    getdateOptions() {
      this.dateOptions = [{
        value: 'date1',
        label: '2016-05-02'
      }, {
        value: 'date2',
        label: '2016-05-04'
      }, {
        value: 'date3',
        label: '2016-05-01'
      }, {
        value: 'date4',
        label: '2016-05-03'
      }]
    },
    getnameOptions() {
      this.nameOptions = [
        {
          value: 'name1',
          label: '王小1'
        }, {
          value: 'name2',
          label: '魏小2'
        }, {
          value: 'name3',
          label: '刘小3'
        }, {
          value: 'name4',
          label: '李小4'
        },
        {
          value: 'name5',
          label: '孙小5'
        }
      ]
    },
    getprovinceOptions() {
      this.provinceOptions = [
        {
          value: 'pro1',
          label: '上海'
        }, {
          value: 'pro2',
          label: '辽宁'
        }, {
          value: 'pro3',
          label: '山西'
        }, {
          value: 'pro4',
          label: '重庆'
        }
      ]
    },
    getcityOptions() {
      this.cityOptions = [
        {
          value: 'city1',
          label: '上海'
        }, {
          value: 'city2',
          label: '丹东'
        }, {
          value: 'city3',
          label: '大同'
        }, {
          value: 'city4',
          label: '重庆'
        }
      ]
    },
    getaddressOptions() {
      this.addressOptions = [
        {
          value: 'addr1',
          label: '上海市普陀区金沙江路 1518 弄'
        }, {
          value: 'addr2',
          label: '辽宁丹东金沙江路 1517 弄'
        }, {
          value: 'addr3',
          label: '山西大同金沙江路 1519 弄'
        }, {
          value: 'addr4',
          label: '重庆市金沙江路 1516 弄'
        }
      ]
    },
    getzipOptions() {
      this.zipOptions = [
        {
          value: 'zip1',
          label: '200331'
        }, {
          value: 'zip2',
          label: '200332'
        }, {
          value: 'zip3',
          label: '200333'
        }, {
          value: 'zip4',
          label: '200334'
        }
      ]
    },
    // 筛选列表
    handleSelect(value, row) {
      // console.log(this.tableSearchParams)
      console.log(Object.entries(this.tableSearchParams))
      //   console.log(Object.values(this.tableSearchParams))
      //   Object.values(this.tableSearchParams).forEach(item => {
      //      if(item !== ''){
      //          this.length++
      //      }
      //   })

      //  console.log(this.tableSearchParams)
      // 在本次循环中 都需要去在当前筛选基础上去筛选 新的循环都需要 从头筛选
      // while(length>0){
      //   this.tableData =  this.tableDataNew.filter((e) => {
      //         return e[item[0]] === item[1]
      //    })
      //    this.length--;
      //    return this.tableData
      //  }

      // 1####
      // Object.entries(this.tableSearchParams).forEach((item) => {
      //   // 在本次循环中 都需要去在当前筛选基础上去筛选 新的循环都需要 从头筛选
      //    if(item[1] !== '') {   
      //     this.tableData =  this.tableDataNew.filter((e) => {
      //           return e[item[0]] === item[1]
      //      })

      //      console.log(this.tableData)
      //      console.log(this.tableDataNew)
      //      return this.tableData
      //    }
      // })
      // 2####
      // 在本次循环中 都需要去在当前筛选基础上去筛选 新的循环都需要 从头筛选
      // this.tableData =  this.tableDataNew.filter((e) => {
      //      let a =  Object.entries(this.tableSearchParams).reduce((arr) => {
      //          if(!!arr &&  arr[1] !== undefined && e[arr[0]] === arr[1]){
      //               return true
      //          }
      //      })
      //     //  console.log(a)
      //      return a

      //  })
      //  return this.tableData

      //3 ##
      this.tableData = this.tableDataNew.filter(item => {
        // 遍历所有查询条件
        for (const [k, v] of Object.entries(this.tableSearchParams)) {
          if (v) { // 如果条件不为空 
            if (!item[k] || !item[k].includes(v)) {
              return false; // 如果当前项不包含查询条件，则过滤掉
            }
          }
        }
        return true; // 如果所有条件都满足，则保留
      });
    }
  }
}
</script>

<style></style>
